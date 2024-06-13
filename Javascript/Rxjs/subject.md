# Overview
![image](https://github.com/LenChang/Tech_Sharing/assets/9037287/91204d53-dc25-4882-8ff4-02700c9f910a)
## Reference
- https://stackoverflow.com/questions/43348463/what-is-the-difference-between-subject-and-behaviorsubject

# asObservable
> The recommended way of TS is only by type casting directly
## Purpose
- You'd need to hide the sequence because you don't want the stream source to **be publicly available** in every component.
```
private messageSubject = new BehaviorSubject<any>(undefined);
public messages$: Observable<any> = this.messageSubject;
```
## Reference 
- https://stackoverflow.com/questions/65121970/should-i-use-asobservable-in-behaviorsubject
- https://stackoverflow.com/questions/36986548/when-to-use-asobservable-in-rxjs
