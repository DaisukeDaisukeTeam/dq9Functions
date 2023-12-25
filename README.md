# dq9Functions

dq9 function name sharing project using [resymgen](https://github.com/UsernameFodder/pmdsky-debug/blob/master/docs/resymgen.md) that comes with [pmdsky-debug](https://github.com/UsernameFodder/pmdsky-debug) project
Currently only a handful of functions from the jp version are provided

It includes some functions for division and decimal point processing, and by sharing them, the purpose is to omit some of the tedious discrimination work.
I'm not going to do a complete analysis.

See the issue for instructions on how to import.
https://github.com/DaisukeDaisukeTeam/dq9Functions/issues/1

## AT
This is the first random number in the game where the 32-bit LCG algorithm is used. It is used for the following purposes
- Monster spawn
- Field-related random numbers
- In-game animations
- Monster treasure chest drops
- Symbol movement direction determination
- Monster determination of encounters at sea
- Drawing lots for too stunned to move

will be updated with the following expression
```
rand = ((rand * 0x41C64E6D) + 0x3039 & 0xFFFFFFFF)
```
<!--
32bit LCGアルゴリズムが採用されているゲーム内の1つ目の乱数です。下記の目的で使用されています。
- モンスタースポーン
- フィールド関連の乱数
- ゲーム内のアニメーション
- モンスターの宝箱ドロップ
- シンボルの移動方向決定
- 海上のエンカウントのモンスター決定
- too stunned to moveの抽選
次の式で更新されます
-->

## BT

It is the second random number in the game and uses a 64-bit LCG algorithm.
In Japan, it is called a Hoimi table.
AT and BT share the same seed value, and in 3ds the initial seed is very narrow and the way it advances is predictable and consistent, allowing the initial seed to be identified and tracked

Some of the intended uses are
- Drawing alchemicals with large alchemical success
- Recovery on feeds
- Rewards from the Demon King or Map Boss
- Lottery for items from the Fountain
- Determination of member's gesture and accompaniment
- Consumed during super special moves
- Lottery for Zaoral
- Lottery for escape
- Lottery for messages of examine command

will be updated with the following expression
```
seed(64bit) = ((seed * 0x5d588b656c078965) + 0x269ec3) & 0xFFFFFFFFFFFFFFFF
```

<!--
ゲームの2番目の乱数で、64-bit LCGアルゴリズムが採用されています。
日本ではホイミテーブルと呼ばれています。
ATとBTは同じシード値を共有し、3dsでは初期シードの幅が非常に狭く、進み方が予測可能で一貫性があるため、初期シードを特定して追跡することができます
使用目的の一部は次の通りです
- 錬金大成功のある錬金の抽選
- フィード上での回復
- 魔王or地図ボスの報酬
- 泉のアイテムの抽選
- メンバーのしぐさ、お供決定
- 超必殺技時に消費する
- ザオラルの抽選
- 逃げるの抽選
- examineコマンドのメッセージ抽選
次の式で更新されます
--!>
