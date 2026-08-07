# Superscaler and ILP(Instrution-Level-Parallelism)
  CPU ရဲ့ architecture နှစ်ခု ဖြစ်တဲ့ CISC  နဲ့ RISC ရဲ့ အားပြိုင်မှုက CPU technology ကို နောက်ထပ် တိုးတက်ဖို့ လမ်းကြောင်းဖောက်ပေးလိုက်တာပါပဲ။ CISC ရော RISC ရောက သုံးတယ့် နည်းပညာရော technique တွေရော မတူကြတော့ ဘယ်ကောင်ပိုကောင်းလည်းဆိုတာကတော့ ပြောဖို့ လိုမနေပါဘူး။ ဒီ topic မှာ RISC ‌ရဲ့ နောက်ပိုင်း  ထွက်ပေါ်လာတဲ့ နည်းပညာ နှစ်ခုဖြစ်တဲ့ ILP(Instructions-level parallelism) နဲ့ Superscalar Processors တွေအကြောင်းကို အကြမ်းဖျင်း ရှင်းပြသွားမှာပါ။
  Superscalar Processors တွေဆိုတာ က သမားရိုးကျ processer တွေမှာ instructions တွေကို pipelining ခွဲပြီး overlapping လုပ်နိုင်တာ ထက် ပိုပါတယ်။ ဒီကောင်တွေက overlapping လုပ်နိုင်တာတင်မကဘဲ instructions တွေကို တစ်ပြိုင်ထဲ တစ်ချိန်ထဲ clock cycle တစ်ခုထဲမှာ အပြိုင် fetch,decode, execute,write လုပ်နိုင်တာပါ။ ပုံမှန် pipelining ‌မှာ overlapping လုပ်ပြီး instructions တွေကို တစ်ပြိုင်ထဲလုပ်နိုင်တယ်ဆိုပေမယ့် instructions A က fetch လုပ်နေတဲ့ အချိန် instructions B က တစ်ပြိုင်ထဲ fetch လုပ်မရပါဘူး clock cycle တစ်ခုမှာ fetch တစ်ခါပဲ လုပ်နိုင်ပါတယ်။ ဒါကြောင့် instructions A decode တဲ့ အချိန်ကျမှ B က fetch လုပ်ရပါတယ်။

superscalar မှာတော့ instructions A ရော B ရောက တစ်ချိန် ထဲမှာ fetch , decode , execute လုပ်နိုင်ပါတယ်။ ဘာလို့ဆို superscalar ရဲ့ pipelining က pipeline တစ်ခုချင်းစီမှာ ကိုယ်ပိုင် ALU တွေသာမက integer အတွက် သပ်သပ် pipeline တွေ float အတွက် သပ်သပ် pipeline တွေဆိုပြီး ခွဲထားတာဖြစ်လို့ပါ။

ဒါကြောင့် superscalar မှာ degree ပေါ်မှုတည်ပြီး instructions ၂ ခုက နေစ သုံးလေးခုကို တစ်ပြိုင်ထဲ process လုပ်နိုင်ပါတယ်။

### Superpipeline 

 Superpipeline နဲ့ Superscalar နဲ့က ခပ်ဆင်ဆင်‌ဆိုပေမယ့် နည်းပညာမတူပါဘူး။ Superpipeline ဆိုတာကတော့ Instructions တစ်ခုလုပ်ရင် လုပ်ရတဲ့  stage 4 ခု ရှိတယ်ဆိုပါဆို့ fetch,decode, execute and write ၊ superpipeline မှာ ဒီ ၄ ခုကို နှစ်ဆ ပြောင်းပစ်ပါတယ် ၊ ဥပမာ f1,f2,d1,d2,e1,e2,w1,w2 ပြီးတော့ ၈ ခု ခွဲလိုက်တယ်ဆိုရင် ၊ Pipeline Stage တစ်ခုစီရဲ့ Delay ကို လျှော့လိုက်တာကြောင့် Internal Clock Frequency ကို မြှင့်နိုင်တာ ဖြစ်တယ်။ fetch က clock cycle တစ်ခုကို f1,f2 ဆိုပြီး နှစ်ခု ခွဲလိုက်ပါတယ်။ ဒီမှာတွေးရမှာ ပိုကြာသွားမှာ မဟုတ်ဘူးလားပေါ့။ ဒါပေမယ့် cpu ရဲ့ architecture အရကိုက clock cycle နည်းလေး မြန်လေပါပဲ။ ဒါကြောင့် pipeline တစ်ခုထဲမှာတင် stage တစ်ခု ကို မြန်မြန်ဆန်ဆန် ဖြတ်သန်းနိုင်ပါတယ်။  internal clock speed ကို နှစ်ဆ တိုးလိုက်တယ့် သဘောပါ။ ဒါကြောင့် performance ပိုကောင်းပါတယ်။
## ILP(Instructions-level-parallelism) 
 ILP ဆိုတာကတော့ program တစ်ခု က instructions ဘယ်လောက်ကို တစ်ပြိုင်ထဲ executed လုပ်နိုင်တဲ့ degree ကိုဆိုလိုတာပါ။ Superscaler နည်းပညာက ILP ဒီ ILP ကို approach လုပ်ထားတာပါပဲ။ ILP degree ကိုမြှင့် ဖို့ဆိုရင် compiler ရဲ့ optimization ရော hardware techniques တွေက ပါ ပူးပေါင်းလုပ်ဆောင်ကြရပါတယ် ။ ဥပမာ Instructions 1,2,3 မှာ Instruction 1 က Instruction 2 ထက် လုပ်ရမှာ independent ဖြစ်တယ် ဆိုရင် Instructions 1 ကို အောက်ချပြီး instructions 2 ကိုအရင်လုပ်တာမျိုးပါ။ ဒါက compiler ရဲ့ order လုပ်ပေးနိုင်မှု ၊instructions တွေကို စစ်နိုင်တာပေါ်နဲ့ ၊ hardware architecture က ကူညီ စစ်ပေးနိုင်တာပေါ်မူတည်ပါတယ်။

ILP မှာ တစ်ပြိုင်ထဲ instructions တွေကို executed လုပ်နိုင်‌တယ်ဆိုပဲမယ့် သူ့မှာလည်း limit တွေတော့ ရှိသေးတာပေါ့။
limitations စုစုပေါင်း 5 ခုရှိပါတယ်။

1. True data dependency 
2. Procedural dependency 
3. Resource conflicts
4. Output dependency 
5. Antidependency တွေဖြစ်ပါတယ်။

1\. True data dependency ဆိုတာကတော့ လွယ်ပါတယ် Instructions နှစ်ခု တစ်ပြိုင်ထဲ လုပ်ရမယ်ဆိုပါစို့ အပေါ်က instructions 1 က ရတယ့် results ကိုမှ instructions 2 က သုံးရမယ်ဆိုရင် data dependency ရှိနေပါပြီ။
```
i1 --> r1 = r2+ r3
i2 --> r4= r1+ r5
```
ဒီ case ကို RAW(Read after Write) လို့လည်းခေါ်သလို flow dependency လို့လည်းခေါ်ပါတယ်။

2\. Procedural dependency ကတော့ Jump,Breach condition တွေကြောင့် ဖြစ်လာတာပါ။ ဥပမာ
Instruction 2 က if == ဘယ်လောက်ဖြစ်မှ jmp မယ် exec လုပ်မယ်ဆိုပြီး ရှိတယ်။ Instructions 1 က တော့ ရိုးရိုးပဲ register နှစ်ခုကိုပေါင်းမယ်။ ပြီးရင်တော့ instructions 3,4,5 ဆိုပြီး ဆက်လာမယ် ပဲထား။ degree 2 အရ I1 ,I2 က clock cycle တစ်ချိန်တည်းမှာ executed လုပ်နိုင်မယ် ။ ဒါပေမယ့် ‌သူတို့ fetch လုပ်ပြီး နောက် clock cycle မှာ တစ်ခါတည်း လိုက် fetch လုပ်ရမယ့်အစား ၊ I2 ရဲ့ conditional jmp ကြောင့် I2 ရော I1 ရော  executeလုပ်ပြီးတယ့် အချိန်ထိ စောင့်ပြီး Write လုပ်တဲ့ cycle ကျမှ fetch လုပ်နိုင်ပါတယ်။ I2 conditional jmp ကြောင့် Branch Result မသိသေးတဲ့အတွက် နောက် Fetch လုပ်မယ့် Instruction ကို မသေချာသေးဘဲ Stall ဖြစ်နိုင်ပါတယ်။
```
I1: CMP R1, R2

I2: BEQ LABEL      ; if R1 == R2, jump

I3: ADD R3, R4, R5

LABEL:
I4: SUB R6, R7, R8
```
3\. Resources Conflict ကတော့ရှင်းတယ်။ instructions နှစ်ခုလုံးက memory တစ်ခု တည်းကို သုံးချင်တဲ့ အချိန်ဆိုဖြစ်ပါတယ်။(memory,cache,buses, register-file ports, functional units) ဥပမာ ALU တစ်ခုကိုတည်းကို Add , Sub နှစ်ခုလုံးက သုံးချင်တာမျိုး ဆို ရင် Add ပြီးမှ Sub က သုံးရမှာဖြစ်တယ်။
ဒီ case က hardware resources ‌တွေနဲ့ ပိုပြီးသက်ဆိုင်ပါတယ်။
```
I1: ADD R1, R2, R3

I2: SUB R4, R5, R6
```
4\. Output Dependency ကတော့ instructions နှစ်ခုလုံးက Register တစ်ခုတည်းကို write ချင်တဲ့ အခါမှာ ဖြစ်ပါတယ်။
I1 ရော I2 ရောက ရတဲ့ results တွေကို Reg1 မှာ Write ချင်တယ်။ compiler optimization အရ order စီပြီး တဲ့ အခါ ဘယ် instructions ကအရင် reg ကို write မယ်ဆိုတာ ပြောင်းသွားတဲ့ အတွက် data မှားနိုင်ပါတယ်။WAW (Write after Write)
```
I1: ADD R1, R2, R3

I2: MUL R1, R4, R5
```

5\. Antidependency ကတော့ ပထမ instructions မှာ read ရမယ့် value က ဒုတိယ instructions ရယ့် write နေရာမှာ ရှိနေတာပါ။ ပြောချင်တာ order မှားသွားရင် i1 လုပ်ဖို့ လိုတယ့် value ကို i2 က change ပစ်လိုက်နိုင်တာမျိုးပါ။WAR (Write after Read )
```
I1: ADD R4, R1, R2

I2: MOV R1, R5
```
### Machine Parallelism
machine parallelism ဆိုတာကတော့ ILP က instructions processer မှာ ပါပြီး တကယ် တစ်ပြိုင်တည်းလုပ်နိုင်တဲ့ pipeline တွေရှိမရှိတင်မက အဲ့ processer က ဘယ်လောက်ထိ instructions တွေကို reorder လုပ်ပေးနိုင်လဲ ၊ independent instructions detect နိုင်လဲ data dependency တွေရှိမရှိနဲ့ breach jmp တွေ resources Conflict တွေကို ဘာ်လိုကိုင်တွယ်မလဲ ဆိုတာတွေ အကုန်ပါဝင်ပါတယ်။

နောက်တစ်ခုကတော့ ordering တွေပါ ။ ILP တွေမှာ fetch ,decode , executed လုပ်ဖို့ အတွက် machine တွေ ကို issue လုပ်ပေးရပါတယ်။ ဒီ issue stage ဟာ instructions decode ပြီးတဲ့ အခါ နဲ့ instructions executed မလုပ်သေးခင် အချိန်ကြားကာလာမှာ  ဆုံးဖြတ်ပေးရတာပါ။


superscalar မှာတော့ issues policies သုံးခုရှိပါတယ်

#### *In order issue with in order completion* 

decode ပြီးတဲ့ i1,i2,i3 တွေဟာ execute တဲ့ အခါမှာလည်း order အတိုင်း execute လုပ်ပြီး memory ပေါ် ပြန် write တဲ့ အခါ order အတိုင်း i1,i2,i3 ပြန် write ပါတယ်။
ဒီ တစ်ခုက ရိုးရှင်းပြီး အကယ်၍ instructions တစ်ခုက လိုတာထက်ကြာ ဖို့ စောင့်ရမယ်ဆိုလည်း stall လုပ်ပြီး စောင့်ပါတယ်။ ဒါပေမယ့် program ကတော့ ပုံမှန်အတိုင်း execute လုပ်ပြီး value တွေက မျှော်မှန်း ထားတဲ့ အတိုင်း ထွက်လာပါတယ်။

#### In order issue with out of order completion 

ဒီ တစ်ခုကတော့ decode ပြီးတော့ order အတိုင်း execute လုပ်တယ်ဆိုပေမယ့် completion ဖြစ်ပြီး memory ပေါ် write တဲ့ အခါ အရင်ပြီးတဲ့ instructions ကို write ပစ်ပါတယ်။ ဒါကြောင့် i1,i2 တစ်ပြိုင်ထဲ လုပ်ပေမယ့် i1 က ကြာလို့ stall ရင် ပြီးတဲ့ i2 ကို memory ပေါ် write ပစ်ပါတယ် ။


#### Out of order issue with Out of order completion 

နောက်ဆုံးတစ်ခု ဖြစ်တဲ့ ဒီကောင်ကတော့
decode လုပ်ပြီးသား instructions တွေကို instructions windows လို့ခေါ်တဲ့ buffer တစ်ခုမှာ သွားရောက် သိမ်းဆည်းပါတယ်။ ပြီးတဲ့‌နောက် execute လုပ်ဖို့ အတွက်  order စီပေးရပါတယ်။ ဥပမာ instruction 1,2 နှစ်ခု decode ပြီးတဲ့ အခါမှာ ဘယ်ကောင်ကို အရင် executed လုပ်ရင် ပိုမြန်မလဲဆိုတာကို စစ်ရတယ် ပြီးမှ execute ပါတယ်။  Write ပြန်လုပ်တဲ့ အခါမှာတော့ အရင်ပြီးတဲ့ instructions ကို အရင် write လုပ်ပါတယ်။ ဒါကြောင့်  instructions တစ်ခုကြာနေရင် stall လုပ်ပြီး နောက် cycle မှ write ပါတယ်။ ဒီ မှာ အဓိကက Instructions windows ကို decode stage ပြီးတဲ့ အခါမှာ သုံးတာပါ။
