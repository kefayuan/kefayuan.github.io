---
layout: page
title: CountDownLatch, CycleBarrier, Phaser
---

CountDownLatch   
..* created with fixed number of threads, CountDownLatch​(int count)
..* can not be reset
..* allows threads to wait(void CountDownLatch.await(), boolean await​(long timeout, TimeUnit unit)) or continue with its execution CountDownLatch.countDown()

CycleBarrier  
..* created with fixed number of threads, CyclicBarrier(int parties) or CyclicBarrier(int parties, Runnable barrierAction)
..* can be void reset() 
..* does not a provide a method for the threads to advance. The threads have to wait til all the threads arriveP
  
  
Phaser
..* number of threads can be changed dynamically, Phaser(),Phaser(int parties), Phaser(Phaser parent, int parties)  
..* can be reset and is reuseable, awaitAdvance(int phase)   
..* allows threads to wait(int awaitAdvance(int phase)) or continue with its execution(int arrive())
..* support mulitple phases
