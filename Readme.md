# Install

```
python3 setup.py install
```

or

```
pip3 install callrate
```

# Usage

``` python
import threading
from callrate import call_rate
import time


@call_rate(7, 10, False)
def test_print(i):
    print("Thread -> {}".format(i))


def test_thread(i):
    while True:
        try:
            test_print(i)
        except:
            pass


def main():
    threads = []
    for i in range(10):
        threads.append(threading.Thread(target=test_thread, args=(i, )))
        threads[-1].start()

    for thread in threads:
        thread.join()

if __name__ == "__main__":
    main()
```

# Warning
Note that the `call_rate` and `CallRate` is thread safe (not process safe)