---
title: test-day-99
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2022-01-11 09:55:39
---
## Today's Task
- [ ] [ASAP] Comment Time
- [ ] [ASAP] Property Page

## Additional Task 
- [ ] Fix Audit Tool
- [x] Fix Component Audit
- [x] Fix Component Audit v4
- [x] Create build jobs

## Thought

### 1

property page 和 comment time 写的实在太慢了

不熟悉呀

### 2

三个 audit 全挂了

两个是因为 Jenkins Job 的 Branch 设置原因，填 `origin/master` 就好了，否则会去找 `InfractionLedger` 的 master branch

sox audit 就很离谱，Cassandra Contactpoint 炸了，不仅仅是 9042 端口没法访问，这台机器本身就连不上去……

```
21:34:17.000 [main] INFO  com.soxaudit.SoxauditApplication - Starting SoxauditApplication v0.0.1-SNAPSHOT with PID 15872 (/root/audittool/soxaudit.jar started by root in /home/shdev/pct/jenkins/workspace/audit_tool/sox-audit/soxaudit)
21:34:17.006 [main] DEBUG com.soxaudit.SoxauditApplication - Running with Spring Boot v2.1.1.RELEASE, Spring v5.1.3.RELEASE
21:34:17.008 [main] INFO  com.soxaudit.SoxauditApplication - No active profile set, falling back to default profiles: default
21:34:27.610 [main] ERROR org.springframework.boot.SpringApplication - Application run failed
org.springframework.beans.factory.UnsatisfiedDependencyException: Error creating bean with name 'gitTools': Unsatisfied dependency expressed through field 'service'; nested exception is org.springframework.beans.factory.UnsatisfiedDependencyException: Error creating bean with name 'recordService': Unsatisfied dependency expressed through field 'dao'; nested exception is org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'recordDAO': Cannot resolve reference to bean 'cassandraTemplate' while setting bean property 'cassandraTemplate'; nested exception is org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'cassandraTemplate' defined in class path resource [com/soxaudit/db/config/CassandraConfig.class]: Bean instantiation via factory method failed; nested exception is org.springframework.beans.BeanInstantiationException: Failed to instantiate [org.springframework.data.cassandra.core.CassandraAdminTemplate]: Factory method 'cassandraTemplate' threw exception; nested exception is org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'sessionFactory' defined in class path resource [com/soxaudit/db/config/CassandraConfig.class]: Bean instantiation via factory method failed; nested exception is org.springframework.beans.BeanInstantiationException: Failed to instantiate [org.springframework.data.cassandra.SessionFactory]: Factory method 'sessionFactory' threw exception; nested exception is org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'session' defined in class path resource [com/soxaudit/db/config/CassandraConfig.class]: Invocation of init method failed; nested exception is com.datastax.driver.core.exceptions.NoHostAvailableException: All host(s) tried for query failed (tried: /10.86.32.167:9042 (com.datastax.driver.core.exceptions.TransportException: [/10.86.32.167:9042] Cannot connect))
```

### 3

中午试着趴了一会，没有睡着

反而又把自己拖进了深渊里

深海下一片漆黑的感觉

甚至还有压强

### 4

LB jobs 迁移 ASAP

原来的机器用了 4~5 年，随时可能会挂

而且 windows 的 Jenkins 会跑起来非常慢

`Build Jobs` -> `OneCase` -> `INTBVT` -> `BVT's` -> `Docker Deploy`

### 5

为啥这个 Ant Button 会换行啊啊啊啊啊啊

<List.Item> 里面会有一个 <List.Item.Meta>，这里面的 AntButton 如果后面没有跟着的 content 就会和 description 一行，

如果有跟着 content 就会换行

我想让它在表格右上角

如果写在 <List.Item> 标签里面的 `extra` 属性里，也会换行…

最离谱的是文档的 SandBox 里面，是在右上角，并不会换行。

然后发现有一个叫 `itemLayout` 的属性，可以设置成 `horizontal` 或者 `vertical`

改成了 `vertical` 就好了……

```typescript
renderCommentRecords(flow: Flow): ReactNode{
        return (
            <Descriptions.Item  label="Comment" span={4}>
                {
                    <List className="demo-loadmore-list"
                        itemLayout="horizontal"
                        locale={ { emptyText: "No comment yet" } }
                        dataSource={flow.comment_records}
                        renderItem={comment =>
                            <List.Item
                                extra={
                                    <AntButton type="link">
                                        Delete
                                    </AntButton>
                                }
                            >
                                <List.Item.Meta
                                    avatar={<Avatar src={comment.avatarURL} size="large" />}
                                    title={comment.user_email}
                                    description={ comment.createTime.format() }
                                    // description={comment.content}
                                />
                                { comment.user_email !== Request.user ? null :
                                    <AntButton type="link" onClick={() => this.deleteComment(comment)}>
                                        Delete
                                    </AntButton>}
                                { comment.content }
                                { comment.user_email !== Request.user ? null :
                                    <AntButton type="link" onClick={() => this.deleteComment(comment)}>
                                        Delete
                                    </AntButton>
                                }
                                { comment.content}
                            </List.Item>
                        }
                    />
                }
                <Comment content={<>
                    <Form<CommentRecord> ref={this.form} onFinish={values => this.postComment(values, flow)}>
                        <Form.Item name="content">
                            <TextArea rows={4}/>
                        </Form.Item>
                        <Form.Item style={ {textAlign: "center" } }>
                            <AntButton type="link" htmlType="submit" loading={this.state.commentButtonLoading}>
                                Add Comment
                            </AntButton>
                        </Form.Item>
                    </Form>
                    </>}
                />
            </Descriptions.Item>
        )
    }
```