## 国密结构

```
#define ECDSAref_MAX_BITS		640 
#define ECDSAref_MAX_LEN		((ECDSAref_MAX_BITS+7) / 8)

typedef struct ECDSArefPublicKey_st
{
	unsigned int  bits;
	unsigned char x[ECDSAref_MAX_LEN]; 
	unsigned char y[ECDSAref_MAX_LEN]; 
} ECDSArefPublicKey;

typedef struct ECDSArefPrivateKey_st
{
	unsigned int  bits;
	unsigned char D[ECDSAref_MAX_LEN];
} ECDSArefPrivateKey;

typedef struct ECDSASignature_st
{
	unsigned char r[ECDSAref_MAX_LEN];	
	unsigned char s[ECDSAref_MAX_LEN];	
} ECDSASignature;
```

