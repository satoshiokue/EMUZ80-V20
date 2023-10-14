# EMUZ80-V20

![MEZV30](https://github.com/satoshiokue/EMUZ80-V20/blob/main/MEZV30.jpeg)    
NEC D70116-8  

電脳伝説さん(@vintagechips)のEMUZ80が出力するZ80 CPU制御信号をメザニンボードで組み替え、V20/V30、8088/8086を動作させることができます。  

動作確認済みCPU  
Intel P8088  
Intel P8086  
NEC D70108C-8  
NEC D70108HCZ-16  
NEC D70116D-8  
NEC D70116C-8  

このソースコードは電脳伝説さんのmain.cを元に改変してGPLライセンスに基づいて公開するものです。

## メザニンボード
https://github.com/satoshiokue/MEZV20 

## 回路図
https://github.com/satoshiokue/MEZV20/blob/main/MEZV20.pdf

## ファームウェア

EMUZ80で配布されているフォルダemuz80.X下のmain.cと置き換えて使用してください。
* emuz80_8086.c
* emuz80_8088.c
* emuz80_V20.c
* emuz80_V30.c

## アドレスマップ
```
Memory
RAM   0x0000 - 0x0FFF  4kB PIC18F47Q43
      0x0000 - 0x1FFF  8kB PIC18F47Q8x
ROM   0x8000 - 0xFFFF 32kB

I/O
通信レジスタ 0x0000
制御レジスタ 0x0001
```

## PICプログラムの書き込み
EMUZ80技術資料8ページにしたがってPICに適合するHEXファイルを書き込んでください。  

またはArduino UNOを用いてPICを書き込みます。  
https://github.com/satoshiokue/Arduino-PIC-Programmer

PIC18F47Q43 emu*_Q43.hex 

PIC18F47Q83 emu*_Q8x.hex  
PIC18F47Q84 emu*_Q8x.hex  

## x86プログラムにつて
ROMにBASICとモニターを格納しています。  
電源投入でUniversal Monitorが起動します。  
モニターに追加したBコマンドによってINTEL8080 Based x86 BASICが起動します。  
BASICから”MONITOR”命令を実行するとUniversal Monitotがコールドスタートします。  
```
MEZV20 2.000MHz

Universal Monitor 8086
V30/V20
] b

INTEL8080 Based x86 BASIC Ver 4.7b
Copyright (C) 1978 by Microsoft
1657 Bytes free
Ok
monitor

Universal Monitor 8086
V30/V20
]
```
INTEL8080 Based x86 BASIC
https://github.com/satoshiokue/8086_NASCOM_BASIC

Universal Monitor  
https://electrelic.com/electrelic/node/1317  

## x86プログラムの格納
インテルHEXデータを配列データ化して配列rom1[]およびrom2[]に格納すると0x8000以降に配置されて実行できます。  

## 謝辞
思い入れのあるCPUを動かすことのできるシンプルで美しいEMUZ80を開発された電脳伝説さんに感謝いたします。

## 参考）EMUZ80
EUMZ80はZ80CPUとPIC18F47Q43のDIP40ピンIC2つで構成されるシンプルなコンピュータです。

![EMUZ80](https://github.com/satoshiokue/EMUZ80-6502/blob/main/imgs/IMG_Z80.jpeg)

電脳伝説 - EMUZ80が完成  
https://vintagechips.wordpress.com/2022/03/05/emuz80_reference  
EMUZ80専用プリント基板 - オレンジピコショップ  
https://store.shopping.yahoo.co.jp/orangepicoshop/pico-a-051.html  
