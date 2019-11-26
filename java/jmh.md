# JMH

**MyBenchmark.java**
```java
import org.openjdk.jmh.Main;
import org.openjdk.jmh.annotations.*;
import org.openjdk.jmh.runner.RunnerException;

import java.io.IOException;

public class MyBenchmark {

    @Benchmark
    @Warmup(iterations = 2)
    @Measurement(iterations = 2)
    @BenchmarkMode(Mode.Throughput)
    @Fork(value = 1, warmups = 1)
    public void init(ExecutionPlan plan) {
        MyObject target = plan.target;
        for (int i = 0; i < plan.numberOfIterations; i++) {
            target.doStuff();
        }
    }

    public static void main(String[] args) throws IOException, RunnerException {
        // run with a single arg that contains this class's `Class::getCanonicalName()`
        Main.main(args);
    }
}
```

**ExecutionPlan.java**
```java
import org.openjdk.jmh.annotations.*;

@State(Scope.Benchmark)
public class ExecutionPlan {

    @Param({
            "100", "200", "300"
    })
    public int numberOfIterations;

    public MyObject target;

    @Setup(Level.Trial)
    public void setup() {
        target = MyObject.create();
    }
}
```

## Resources

- https://www.baeldung.com/java-microbenchmark-harness
