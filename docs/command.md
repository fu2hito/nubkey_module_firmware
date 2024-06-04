# nubkey_module　通信仕様

## 0x60　製品の情報取得

<b>■ 送信 ： 1 byte </b>
|  内容  |  説明  |  サイズ(byte)  |
|  --  |  --  |  --  |
|  コマンドタイプ  |  0x60 (固定)  |  1  |

<b>■ レスポンス ： 3 byte </b>
|  内容  |  説明  |  サイズ(byte)  |
|  --  |  --  |  --  |
|  I2Cアドレス  |  nubkey_moduleのI2Cアドレス  |  1  |
|  製品番号  |  nubkey_moduleの識別番号（0x20 固定）  |  1  |
|  ファームウェアバージョン  |  使用されているファームウェアのバージョン  |  1  |

<br><br>


## 0x40　I2Cアドレスを変更する
nubkey_moduleのI2Cアドレスを変更して、nubkey_moduleを再起動します。<br>
<b>■ 送信 ： 2 byte </b>
|  内容  |  説明  |  サイズ(byte)  |
|  --  |  --  |  --  |
|  コマンドタイプ  |  0x40 (固定)  |  1  |
|  I2Cアドレス  |  変更後のI2Cアドレス  |  1  |

<b>■ レスポンス ： 1 byte </b>
|  内容  |  説明  |  サイズ(byte)  |
|  --  |  --  |  --  |
|  コマンドのエコー  |  0x40（固定）  |  1  |

<br><br>


## 0x41　設定内容を取得する

<b>■ 送信 ： 1 byte </b>
|  内容  |  説明  |  サイズ(byte)  |
|  --  |  --  |  --  |
|  コマンドタイプ  |  0x41 (固定)  |  1  |

<b>■ レスポンス ： 23 byte </b>
|  内容  |  説明  |  サイズ(byte)  |
|  --  |  --  |  --  |
|  コマンドのエコー  |  0x41  |  1  |
|  I2Cアドレス  |  nubkey_moduleのI2Cアドレス  |  1  |
|  nubkey_off_status  |  Nubkey_offにするかどうか<br>(0=Nubkey OFF / 1=Nubkey ON / 2=ピンの情報優先)  |  1  |
|  key_actuation  |  Nubkey_off時のアクチュエーションポイント  |  2  |
|  nub_start_time  |  Nubkeyとしてマウス操作させるまでの時間(ミリ秒)  |  2  |
|  nub_start_down  |  Nubkey マウス移動開始させるアクチュエーションポイント  |  2  |
|  nub_speed_left  |  Nubkey マウス移動させる速度 左  |  2  |
|  nub_speed_right  |  Nubkey マウス移動させる速度 右  |  2  |
|  nub_speed_up  |  Nubkey マウス移動させる速度 上  |  2  |
|  nub_speed_down  |  Nubkey マウス移動させる速度 下  |  2  |
|  rang_x  |  キャリブレーション中心の X 座標  |  2  |
|  rang_y  |  キャリブレーション中心の Y 座標  |  2  |
|  loop_delay  |  入力読み込みサイクルのdelay値(ミリ秒)  |  2  |

<br><br>


## 0x42　Nubkey OFF モードの設定
Nubkey OFF モードを設定して EEPROM に保存します。<br>
<b>■ 送信 ： 2 byte </b>
|  内容  |  説明  |  サイズ(byte)  |
|  --  |  --  |  --  |
|  コマンドタイプ  |  0x42 (固定)  |  1  |
|  モード  |  0=Nubkey OFF / 1=Nubkey ON / 2=ピンの情報優先  |  1  |

<b>■ レスポンス ： 1 byte </b>
|  内容  |  説明  |  サイズ(byte)  |
|  --  |  --  |  --  |
|  コマンドのエコー  |  0x42  |  1  |

<br><br>


## 0x43　アクチュエーションポイント設定
アクチュエーションポイント設定してEEPROMに保存します。<br>
※ このアクチュエーションポイントは Nubkey OFF モードの時に使用されます。<br>
<b>■ 送信 ： 3 byte </b>
|  内容  |  説明  |  サイズ(byte)  |
|  --  |  --  |  --  |
|  コマンドタイプ  |  0x43 (固定)  |  1  |
|  アクチュエーションポイント  |  キーをONにする高さを指定<br>ここで指定した高さを下回るとキーがONになります。  |  2  |

<b>■ レスポンス ： 1 byte </b>
|  内容  |  説明  |  サイズ(byte)  |
|  --  |  --  |  --  |
|  コマンドのエコー  |  0x43  |  1  |

<br><br>


## 0x44　Nubkey 開始までの時間を設定
Nubkeyとしてマウス操作させるまでの時間を更新してEEPROMに保存します。<br>
ここで指定した時間より短い時間でキーを離すと、タップ判定となりキーONが送信されます。<br>
<b>■ 送信 ： 2 byte </b>
|  内容  |  説明  |  サイズ(byte)  |
|  --  |  --  |  --  |
|  コマンドタイプ  |  0x44 (固定)  |  1  |
|  時間  |  Nubkey 開始までの時間（ミリ秒）  |  2  |

<b>■ レスポンス ： 1 byte </b>
|  内容  |  説明  |  サイズ(byte)  |
|  --  |  --  |  --  |
|  コマンドのエコー  |  0x44  |  1  |

<br><br>


## 0x45　Nubkey を動かし始める高さを設定
Nubkey 動かし始める高さを変更してEEPROMに保存します。<br>
<b>■ 送信 ： 3 byte </b>
|  内容  |  説明  |  サイズ(byte)  |
|  --  |  --  |  --  |
|  コマンドタイプ  |  0x45 (固定)  |  1  |
|  高さ  |  200～400  |  2  |

<b>■ レスポンス ： 1 byte </b>
|  内容  |  説明  |  サイズ(byte)  |
|  --  |  --  |  --  |
|  コマンドのエコー  |  0x45  |  1  |

<br><br>

## 0x46　Nubkey マウス移動の速度設定
Nubkeyとしてマウス操作させる速度を更新してEEPROMに保存します。<br>
<b>■ 送信 ： 9 byte </b>
|  内容  |  説明  |  サイズ(byte)  |
|  --  |  --  |  --  |
|  コマンドタイプ  |  0x46 (固定)  |  1  |
|  移動速度 左  |  移動速度　0～32767  |  2  |
|  移動速度 右  |  移動速度　0～32767  |  2  |
|  移動速度 上  |  移動速度　0～32767  |  2  |
|  移動速度 下  |  移動速度　0～32767  |  2  |

<b>■ レスポンス ： 1 byte </b>
|  内容  |  説明  |  サイズ(byte)  |
|  --  |  --  |  --  |
|  コマンドのエコー  |  0x46  |  1  |

<br><br>


## 0x47　Nubkey 読み込みサイクルのdelay値設定
Nubkey 読み込みサイクルのdelay値を変更してEEPROMに保存します。<br>
<b>■ 送信 ： 3 byte </b>
|  内容  |  説明  |  サイズ(byte)  |
|  --  |  --  |  --  |
|  コマンドタイプ  |  0x47 (固定)  |  1  |
|  時間  |  停止する時間（ミリ秒）  |  2  |

<b>■ レスポンス ： 1 byte </b>
|  内容  |  説明  |  サイズ(byte)  |
|  --  |  --  |  --  |
|  コマンドのエコー  |  0x47  |  1  |

<br><br>


## 0x48　設定を全てリセットして再起動
<b>■ 送信 ： 1 byte </b>
|  内容  |  説明  |  サイズ(byte)  |
|  --  |  --  |  --  |
|  コマンドタイプ  |  0x48 (固定)  |  1  |

<b>■ レスポンス ： 1 byte </b>
|  内容  |  説明  |  サイズ(byte)  |
|  --  |  --  |  --  |
|  コマンドのエコー  |  0x48  |  1  |

<br><br>


## 0x50　Nubkey のアナログ情報を取得
<b>■ 送信 ： 1 byte </b>
|  内容  |  説明  |  サイズ(byte)  |
|  --  |  --  |  --  |
|  コマンドタイプ  |  0x50 (固定)  |  1  |

<b>■ レスポンス ： 7 byte </b>
|  内容  |  説明  |  サイズ(byte)  |
|  --  |  --  |  --  |
|  コマンドのエコー  |  0x50  |  1  |
|  X座標  |  Nubkey の現在のX座標  |  2  |
|  Y座標  |  Nubkey の現在のY座標  |  2  |
|  高さ  |  キーの押し込み現在の高さ  |  2  |

<br><br>


## 0x51　ホールセンサーの情報を取得
<b>■ 送信 ： 1 byte </b>
|  内容  |  説明  |  サイズ(byte)  |
|  --  |  --  |  --  |
|  コマンドタイプ  |  0x51 (固定)  |  1  |

<b>■ レスポンス ： 9 byte </b>
|  内容  |  説明  |  サイズ(byte)  |
|  --  |  --  |  --  |
|  コマンドのエコー  |  0x51  |  1  |
|  アナログ値  |  ホールセンサーのアナログ値 上  |  2  |
|  アナログ値  |  ホールセンサーのアナログ値 下  |  2  |
|  アナログ値  |  ホールセンサーのアナログ値 左  |  2  |
|  アナログ値  |  ホールセンサーのアナログ値 右  |  2  |

<br><br>

