# enes
c dilinde fizik uzay simülasyonu deneyi
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <math.h>

#define PI 3.14159265

void serbestDusme(double* g, char** ad);
void yukariAtis(double* g, char** ad);
void agirlikHesapla(double* g, char** ad);
void potansiyelEnerji(double* g, char** ad);
void hidrostatikBasinc(double* g, char** ad);
void kaldirmaKuvveti(double* g, char** ad);
void sarkacPeriyodu(double* g, char** ad);
void ipGerilmesi(double* g, char** ad);
void asansorDeneyi(double* g, char** ad);

int main() {

    char isim[40];
    int secim = 0;
    int i;   

    double g[8] = {3.7,8.87,9.81,3.71,24.79,10.44,8.69,11.15};
    char* gezegenler[8] = {"Merkur","Venus","Dunya","Mars","Jupiter","Saturn","Uranus","Neptun"};

    printf("Isim gir: ");
    scanf("%39s", isim);




    while ((secim != -1) ? 1 : 0)
    {
        printf("\n%s secim yap\n", isim);
        printf("1 Dusme  2 Atis  3 Agirlik\n");
        printf("4 Enerji 5 Basinc 6 Kaldirma\n");
        printf("7 Sarkac 8 Ip 9 Asansor\n");
        printf("-1 Cikis\n");
        scanf("%d", &secim);

       switch (secim) {
    case 1:
        serbestDusme(g, gezegenler);
        break;
    case 2:
        yukariAtis(g, gezegenler);
        break;
    case 3:
        agirlikHesapla(g, gezegenler);
        break;
    case 4:
        potansiyelEnerji(g, gezegenler);
        break;
    case 5:
        hidrostatikBasinc(g, gezegenler);
        break;
    case 6:
        kaldirmaKuvveti(g, gezegenler);
        break;
    case 7:
        sarkacPeriyodu(g, gezegenler);
        break;
    case 8:
        ipGerilmesi(g, gezegenler);
        break;
    case 9:
        asansorDeneyi(g, gezegenler);
        break;
    case -1:
        printf("Cikiliyor...\n");
        break;
    default:
        printf("Yanlis secim\n");
        break;
}
    }

    return 0;
}



void serbestDusme(double* g, char** ad)
{
    double t;
    printf("sure: ");
    scanf("%lf",&t);
    t = (t < 0) ? -t : t;

    for(int i=0;i<8;i++)
        printf("%s %.2f m\n",ad[i],0.5*g[i]*t*t);
}

void yukariAtis(double* g, char** ad)
{
    double v0;
    printf("hiz: ");
    scanf("%lf",&v0);
    v0 = (v0 < 0) ? -v0 : v0;

    for(int i=0;i<8;i++)
        printf("%s %.2f m\n",ad[i],(v0*v0)/(2*g[i]));
}

void agirlikHesapla(double* g, char** ad)
{
    double m;
    printf("kutle: ");
    scanf("%lf",&m);
    m = (m < 0) ? -m : m;

    for(int i=0;i<8;i++)
        printf("%s %.2f N\n",ad[i],m*g[i]);
}

void potansiyelEnerji(double* g, char** ad)
{
    double m,h;
    printf("m ve h: ");
    scanf("%lf %lf",&m,&h);

    m = (m<0)?-m:m;
    h = (h<0)?-h:h;

    for(int i=0;i<8;i++)
        printf("%s %.2f J\n",ad[i],m*g[i]*h);
}

void hidrostatikBasinc(double* g, char** ad)
{
    double d,y;
    printf("yogunluk ve derinlik: ");
    scanf("%lf %lf",&d,&y);

    for(int i=0;i<8;i++)
        printf("%s %.2f Pa\n",ad[i],d*g[i]*y);
}

void kaldirmaKuvveti(double* g, char** ad)
{
    double d,v;
    printf("yogunluk hacim: ");
    scanf("%lf %lf",&d,&v);

    for(int i=0;i<8;i++)
        printf("%s %.2f N\n",ad[i],d*g[i]*v);
}

void sarkacPeriyodu(double* g, char** ad)
{
    double L;
    printf("ip: ");
    scanf("%lf",&L);
    L = (L<0)?-L:L;

    for(int i=0;i<8;i++)
        printf("%s %.2f s\n",ad[i],2*PI*sqrt(L/g[i]));
}

void ipGerilmesi(double* g, char** ad)
{
    double m;
    printf("kutle: ");
    scanf("%lf",&m);

    for(int i=0;i<8;i++)
        printf("%s %.2f N\n",ad[i],m*g[i]);
}

void asansorDeneyi(double* g, char** ad)
{
    double m,a;
    int yon;
    printf("m ve a: ");
    scanf("%lf %lf",&m,&a);
    printf("1 yukari 2 asagi: ");
    scanf("%d",&yon);

    m = (m<0)?-m:m;
    a = (a<0)?-a:a;

    for(int i=0;i<8;i++)
        printf("%s %.2f N\n",ad[i],
               (yon==1)?m*(g[i]+a):m*(g[i]-a));

               
}
