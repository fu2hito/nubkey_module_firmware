# nubkey_module_tester vial firmware

このリポジトリは @palette-system による[nubkey_module_tester](https://github.com/palette-system/nubkey_module)のqmkファームウェアを勝手に[vial](https://vial.rocks/)対応させたものです。

## Changes

* Vial対応のための変更を行いました（参考[1,2]）。
* ファームウェアのビルドは`vial-qmk`の作成時点の最新のコミットである`b02ff548caaaafd0ace516257bd93211f74e13eb`を使用しました（参考[3]）。
* Pro Micro RP2040と呼ばれるRP2040ベースのコントローラーボードを使用します（参考[4]）。

## Note

* すべての機能については動作確認を行っていません。
* 当リポジトリの内容についての問い合わせを @palette-system にすることはお控えください。

## Reference

以下のリンクを参考にしました。作成者各位に感謝します。

1. [Build support 1 - Create JSON - Vial](https://get.vial.today/docs/porting-to-via.html)
2. [vial-qmk/keyboards/vial_example/vial_rp2040 at vial · vial-kb/vial-qmk](https://github.com/vial-kb/vial-qmk/tree/vial/keyboards/vial_example/vial_rp2040)
3. [darakuneko/gpk_fwbuilder](https://github.com/darakuneko/gpk_fwbuilder)
4. [Pro Microに代わる新たなコントローラーボード登場！RP2040のボードとは？ - kuriharaのブログ](https://kurihara.hatenadiary.jp/entry/Pro_Micro_RP2040) 

## License

[MIT License](LICENSE)
