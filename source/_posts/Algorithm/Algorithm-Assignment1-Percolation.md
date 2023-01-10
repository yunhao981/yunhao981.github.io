---
title: Algorithm-Assignment1-Percolation
show: true
date: 2019-11-13 14:10:50
categories: Algorithm
tags: Algorithm
description:
---
[Specification](https://coursera.cs.princeton.edu/algs4/assignments/percolation/specification.php)

Trying to do Algortihm Course Assignments.
Finished it long time ago.
So I don't remember too much about the details.

Percolation.java
```java
import edu.princeton.cs.algs4.WeightedQuickUnionUF;

public class Percolation {
    private boolean[] open;
    private int openSites;
    private final int size;
    private final WeightedQuickUnionUF wquf;

    // create n-by-n grid, with all sites blocked
    public Percolation(int n) {
        if (n <= 0)throw new java.lang.IllegalArgumentException();
        this.size = n;
        this.openSites = 0;
        this.open = new boolean[n*n];
        this.wquf = new WeightedQuickUnionUF(n*n + 2);
    }

    private int map2dTo1d(int row, int col) {
        return (row - 1) * size + col;
    }

    private boolean indicesValid(int row, int col) {
        return (row > 0 && row <= size && col > 0 && col <= size);
    }

    // open site (row, col) if it is not open already
    public void open(int row, int col) {
        if (!indicesValid(row, col)) throw new java.lang.IllegalArgumentException();
        int index = map2dTo1d(row, col);
        if (row == 1) {
            wquf.union(0, index);
            open[index-1] = true;
        } else if (row == size) {
            wquf.union(size * size + 1, index);
            open[index-1] = true;
        }

        int left = col-1;
        int right = col+1;
        int up = row-1;
        int down = row+1;

        if (indicesValid(row, left) &&  isOpen(row, left)) {
            wquf.union(index - 1, index);
            open[index-1] = true;
        }

        if (indicesValid(row, right) && isOpen(row, right)) {
            wquf.union(index + 1, index);
            open[index-1] = true;
        }

        if (indicesValid(up, col) && isOpen(up, col)) {
            wquf.union(index - size, index);
            open[index-1] = true;
        }

        if (indicesValid(down, col) && isOpen(down, col)) {
            wquf.union(index + size, index);
            open[index-1] = true;
        }

        if (indicesValid(row, col)) {
            open[index-1] = true;
            openSites++;
        }

    }

    // is site (row, col) open?
    public boolean isOpen(int row, int col) {
        if (!indicesValid(row, col))
            throw new java.lang.IllegalArgumentException();
        return open[(row - 1) * size + col -1];
    }

    // is site (row, col) full?
    public boolean isFull(int row, int col) {
        if (!indicesValid(row, col))
            throw new java.lang.IllegalArgumentException();
        return wquf.connected((row - 1) * size + col, 0);
    }

    // number of open sites
    public int numberOfOpenSites() {
       return openSites;
    }

    // does the system percolate?
    public boolean percolates() {
        return wquf.connected(0, size * size + 1);
    }

    // test client (optional)
    // public static void main(String[] args) {
    //
    // }
}
```


PercolationStats.java
```java

import edu.princeton.cs.algs4.StdOut;
import edu.princeton.cs.algs4.StdRandom;
import edu.princeton.cs.algs4.StdStats;

public class PercolationStats {
    private static final double CONFIDENCE_95 = 1.96;
    private final int trials;
    private final double mean;
    private final double stddev;
    public PercolationStats(int n, int trials) {
        if (n <= 0 || trials <= 0)throw new java.lang.IllegalArgumentException();
        this.trials = trials;
        double[] results = new double[trials];
        for (int i = 0; i < trials; i++) {
            Percolation p = new Percolation(n);
            double count = 0;
            while (!p.percolates()) {
                count++;
                int row = StdRandom.uniform(1, n + 1);
                int col = StdRandom.uniform(1, n + 1);
                while (p.isOpen(row, col)) {
                    row = StdRandom.uniform(1, n + 1);
                    col = StdRandom.uniform(1, n + 1);
                }
                p.open(row, col);
            }
            results[i] = count / (n * n);
        }
        this.mean = StdStats.mean(results);
        this.stddev = StdStats.stddev(results);
    }
    public double mean() {
        return this.mean;
    }
    public double stddev() {
        return this.stddev;
    }
    public double confidenceLo() {
        return mean() - CONFIDENCE_95 * stddev() / Math.sqrt(trials);
    }
    public double confidenceHi() {
        return mean() + CONFIDENCE_95 * stddev() / Math.sqrt(trials);
    }
    public static void main(String[] args) {
        int n = Integer.parseInt(args[0]);
        int t = Integer.parseInt(args[1]);
        PercolationStats ps = new PercolationStats(n, t);
        // StdOut.print(ps.mean());
        // StdOut.print(ps.stddev());
        // StdOut.print(ps.confidenceLo());
        // StdOut.print(ps.confidenceHi());
        StdOut.println("mean                    = " + ps.mean());
        StdOut.println("stddev                  = " + ps.stddev());
        StdOut.println("95% confidence interval = [" + ps.confidenceLo() + ", " + ps.confidenceHi() + "]");

    }
}
```

