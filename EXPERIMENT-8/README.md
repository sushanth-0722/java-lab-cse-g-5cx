## Experiment-8a
## Title:To write program illustrating Daemon Threads
## SourceCode:
``` java
class DaemonThread extends Thread {
   public void run() {
        while(true) {
            try {
                System.out.println("Daemon thread is running");
                Thread.sleep(500);
            } catch(Exception e) {
                System.out.println("Exception occurred");
            }
        }
    }
}
class UserThread extends Thread {
   public void run() {
        for(int i = 0; i <= 5; i++) {
            System.out.println("User thread iteration: " + i);
            try {
                Thread.sleep(1000);
            } catch(Exception e) {
                System.out.println("Exception occurred");
            }
        }
    }
}
class TestDaemon {
    public static void main(String[] args) {

        UserThread userThread = new UserThread();
        DaemonThread daemonThread = new DaemonThread();

        daemonThread.setDaemon(true);

        userThread.start();
        daemonThread.start();

        System.out.println("Main thread continues after task is completed");
    }
}
```
## Output:
![Exp-8a output](exp8a.png)

## Experiment-8b
## Title:Implements Producer Consumer problem using Inter Thread Communication
## SourceCode:
``` java
class SharedBuffer {

    int[] buffer = new int[10];
    int count = 0;
    int in = 0;
    int out = 0;

    synchronized void produce(int item) throws InterruptedException {
        while(count == buffer.length)
            wait();

        buffer[in] = item;
        in = (in + 1) % buffer.length;
        count++;
        notify();
    }

    synchronized int consume() throws InterruptedException {
        while(count == 0)
            wait();

        int item = buffer[out];
        out = (out + 1) % buffer.length;
        count--;
        notify();
        return item;
    }
}
class Producer extends Thread {

    private SharedBuffer buffer;

    Producer(SharedBuffer buffer) {
        this.buffer = buffer;
    }

    public void run() {
        for(int i = 0; i <= 10; i++) {
            try {
                buffer.produce(i);
                System.out.println("Produced: " + i);
            } catch(InterruptedException e) {
                System.out.println("Exception occurred");
            }
        }
    }
}
class Consumer extends Thread {

    private SharedBuffer buffer;

    Consumer(SharedBuffer buffer) {
        this.buffer = buffer;
    }

    public void run() {
        for(int i = 0; i <= 10; i++) {
            try {
                int item = buffer.consume();
                System.out.println("Consumed item " + item);
            } catch(InterruptedException e) {
                System.out.println("Exception occurred");
            }
        }
    }
}
class Main {

    public static void main(String args[]) {

        SharedBuffer buffer = new SharedBuffer();

        Producer p = new Producer(buffer);
        Consumer c = new Consumer(buffer);

        c.start();
        p.start();
    }
}
```
## Output:
![Exp-8b output](exp8b.png)
