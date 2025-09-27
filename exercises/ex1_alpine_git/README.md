# Exercise 1 — Alpine + Git

```
docker build -t ex1 .
docker tag ex1:latest ex1:v0.1
docker run -itd --name ex1c ex1 sh
docker attach ex1c
git --version
```
