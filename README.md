# MyUnixFileSystem-C-App
Implement My Own Unix File System on C like Real Unix File System (Inode, Linking ...)

## Unix File System Structure


<img src="https://user-images.githubusercontent.com/88016041/127095128-f9c45224-fe22-484c-b433-b0df230d2276.png">



## Overview Code 

### Header

```C

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <time.h>
#include <math.h>

struct d_block{
	int num; // 데이터블록 번호
	unsigned char data[128];
}dblock;

struct inode{
	int file_type;
	char file_date[30];
	int file_size;
	int dir;
	int sin;
	int dou;
	int num;
	int numP;
	int numS;
	struct d_block *db;
	struct d_block *sidb;
	struct d_block *didb;
};

struct s_block{
	unsigned imask, dmask1, dmask2;
};

struct my_file_system{
	unsigned b_block : 16;
	struct s_block super[16];
	struct inode *inode[512];
	struct d_block *block[1024];
};

struct dtree{
	int inode;
	char name[5];
	struct inode *p;
	struct dtree *left;
	struct dtree *right;
};

struct btree{
	struct d_block *p;
	struct btree *next;

};

struct my_file_system *mfs;

struct dtree *D=NULL;
struct dtree *cur = NULL;
struct dtree *back = NULL;
struct dtree *back2 = NULL;
struct dtree *back3 = NULL;
struct dtree *back4 = NULL;

```

### Function
```C

void prompt(char [], char [],char [],char []);
void command(char [], char [],char [],char []);
int i_bit_check();
int d_bit_check();
void i_bit_insert();
void d_bit_insert();
void i_bit_del(int);
void d_bit_del(int);
void d_bit_del_func(int);
void cal_date(int);
int cal_size(char []);
void set_sidbit(char [],int);
int* get_sidbit(int);
int *get_sidbit_ADD(int);
void make_sid(int);
void set_didbit(int);
int* get_didbit(int);
void set_dsidbit(int);
int* get_dsidbit(int);
void make_did(int);
void in_data(char [],int);
void sin_data(char [],int,int);
void dsin_data(char [],int,int);
void in_dir(char [],int);
void mymkdir(char []);
int mycd(char []);
int mycd_func(char []);
void myls(char []);
void myls_func(char [],char []);
void swap(char **,int);
void swap2(char **,int [],int);
void myrmdir(char []);
void myrmdir_func(char []);
void mytree(struct dtree*,int);
void mytree_func(struct dtree*,int);
void myshowinode(char []);
void myshowblock(char []);
void mystate();
void mycpfrom(char[],char[]);
void mytouch(char []);
void mytouch_func(char []);
void mycat(char []);
void mycpto(char [],char []);
void mycp(char [],char []);
void mymv(char [],char []);
int mymv_func(char []);
void myshowfile(char [],char [],char []);
void myrm(char []);
void myrm_func(char []);
void myrm_func2(char [],int);

```
