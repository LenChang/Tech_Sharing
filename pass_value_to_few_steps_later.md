---
tags: case_study
--- 

# RxJS: Pass valur to few steps later

```
const getAAA$ = this.aaaService.getAaaList(this.PROJECT_ID);

const getBBBInfo$ = getAAA$.pipe(
    filter((x: tmpA[]) => x && x.length !== 0),
    switchMap((models: tmpA[]) =>
        this.aaaService.getBBB('AAA').pipe(
            map((photos: TT) => ({ photos, models })))
    ),
    switchMap(({ models, photos }) => {
        const modelIds = models.map((x) => x.model_id);
        return this.aaaService
          .CC(modelIds)
          .pipe(
              map((zzArr: ZZ[]) => ({ zzArr, models, photos })));
      }));

const UUU$ = getGatesInfo$.pipe(
      map(({ models, photos, zzArr }) => ({
        ...
      })),
      map(({ zzArr, images }) =>
        ...
      )
    );

UUU$.subscribe((result) =>
      ...
    );
```