---
title: java-spring-boot-1
categories: Java
tags: Java
description: Spring Boot Demo with JPA
show: true
date: 2022-05-25 01:13:04
---

试着跟着教程写了个超级简单的 CRUD api

自上而下是 API Layer, Service Layer, Data Access Layer,

DB 用了 PostgreSQL

# API Layer: Controller

`@RestController`

`@RequestMapping(path = "api/v1/student")`

```java
@Autowired
public StudentController(StudentService studentService) {
    this.studentService = studentService
}
```

CRUD 四天王：

`@GetMapping`

`@PostMapping`

`@DeleleMapping`

`@PutMapping`

注解的类里面调用 service类对象的方法，把参数传过去执行

为啥需要特地分一层出来？

可能是因为这一层描述需要做什么，而 Service 层用来定义具体怎么做

# Service Layer: Service

需要用到 `@Service` 注解整个类

同样的，`@Autowired` 注解构造方法，然后喂给它一个 Repository 对象当参数

repository 对象有好多省力的方法，existsById，findById，findAll 啥的

这里用到了 `@Transactional` 注解，然后原来 java 也有箭头函数的糖吃？

```java
@Transactional
    public void updateStudent(Long studentId, String name, String email) {
        Student student = studentRepository.findById(studentId).orElseThrow(
                () -> new IllegalStateException(
                        "student with id " + studentId + " does not exists"
                )
        );
        if (name != null && name.length() > 0 && !Objects.equals(student.getName(), name)) {
            student.setName(name);
        }
        if (email != null && email.length() > 0 && !Objects.equals(student.getEmail(), email)) {
            Optional<Student> studentOptional = studentRepository.findStudentByEmail(email);
            if (studentOptional.isPresent()) {
                throw new IllegalStateException("email taken");
            }
            student.setEmail(email);
        }
    }
```

# Data Access Layer: Repository, Config, Student

`@Repository` 注解也是需要的

StudentRepository 是个接口而不是具体的类，扩展 JpaRepository<对象类, 主键类>

可能是为了方便写 sql 吧… 第一次见到的语法

```java
@Repository
public interface StudentRepository
        extends JpaRepository<Student, Long> {

    // SELECT * FROM STUDENT WHERE EMAIL=email;
    @Query("SELECT s FROM Student s WHERE s.email = ?1")
    Optional<Student> findStudentByEmail(String email);

}
```

Config 需要注解 `@Configuration`

这个示例里面，是用了 CommandLineRunner 去返回一个箭头函数，里面写死了两个 Student 类的对象，再用了 repository.saveAll 去保存 Student 类的数组

Student 类本身需要 `@Entity` 和 `@Table` 

```java
@Id
@SequenceGenerator(
        name = "student_sequence",
        sequenceName = "student_sequence",
        allocationSize = 1
)
@GeneratedValue(
        strategy = GenerationType.SEQUENCE,
        generator = "student_sequence"
)
```

这段没看懂… 有点序列化那意思？后面再去看看 JPA 的教程

另外，age 是在 Getter 里算出来的，注解了 `@Transient`

# 杂项

application.properties 里面可以指定端口 `server.port`

可以指定 datasource url，username，pswd，

还有涉及到 hibernate 的 ddl-auto, show-sql, dialect 之类

idea 可以在 controller 里面当场测 api，但如果跑在本地还设置了代理会 500

postgres 建库完需要给用户授予权限

`grant all privileges on database "student" to postgres;`

