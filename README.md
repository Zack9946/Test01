/* 家庭用電 */
#define TypeA1 2.5      /* 家庭用電100度以下，每度2.5元 */
#define TypeA2 3.3      /* 家庭用電101度以上，300度以下，每度3.3元 */
#define TypeA3 4.2      /* 家庭用電301度以上，每度4.2元 */

/* 工業用電 */
#define TypeB1 150      /* 工業用電契約馬力，每馬力150元 */
#define TypeB2 1.9      /* 工業用電每度1.9元 */

/* 營業用電 */
#define TypeC1 6        /* 營業用電300度以下，每度6元 */
#define TypeC2 6.8      /* 營業用電301度以上，每度6.8元 */

main(void) {
    int T;          /* 用電類別 */
    float Deg;      /* 用電度數 */
    float C;        /* 工業用電契約馬力 */
    float Fee;      /* 電費 */

    printf("1. 家庭用電");
    printf("\n");
    printf("2. 工業用電");
    printf("\n");
    printf("3. 營業用電");
    printf("\n");

    printf("請輸入用電類別(1~3): ");
    scanf("%d", &T);

    if (T>=1 && T<=3) {
        printf("用電度數= ");
        scanf("%f", &Deg);
        switch(T) {
        case 1: 
            if (Deg<=100)
                Fee = Deg*TypeA1;
            else if (Deg<=300)
                Fee = (Deg-100)*TypeA2 + 100*TypeA1;
            else
                Fee = (Deg-300)*TypeA3 + 200*TypeA2 + 100*TypeA1;
            break;
        case 2:
            printf("契約馬力= ");
            scanf("%f", &C);
            Fee = C*TypeB1 + Deg*TypeB2;
            break;
        case 3:
            if (Deg<=300)
                Fee = Deg*TypeC1;
            else
                Fee = (Deg-300)*TypeC2 + 300*TypeC1;
            break;
        }
        printf("電費共為%f", Fee);
        printf("\n");
    } else {
        printf("類別錯誤!");
        printf("\n");
    }
}
