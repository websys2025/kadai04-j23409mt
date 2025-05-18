[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/q1RWxQjY)
[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=19535591&assignment_repo_type=AssignmentRepo)
## 第4講目の演習課題
すみません。課題を出す場所が分からなかったのでここに書きます。課題を出す場所が違う為減点対象にしてもかまわないので課題を見てください。
### 課題4-1．以下の要件を満たすように kadai4.html を修正せよ。
* 商品用クラス「Item」を完成させて、期待される出力例がコンソールに表示されることを確認せよ。
* 「課題４－１,
* <!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="utf-8">
    <title>演習課題4：自動販売機（クラス）</title>
</head>
<body>
    <h1 id="vending-machine">自動販売機システム</h1>
    <table id="item_area" border="1"></table>
    <script>
        // 商品一覧を記録する連想配列の配列
        const items =  [
            { id: 1, name: "緑茶", price: 140, stock: 5 },
            { id: 2, name: "水", price: 100, stock: 14 },
            { id: 3, name: "オレンジジュース", price: 150, stock: 7 },
            { id: 4, name: "リンゴジュース", price: 150, stock: 9 },
            { id: 5, name: "炭酸水", price: 120, stock: 1 },
            { id: 6, name: "サイダー", price: 160, stock: 3 },
            { id: 7, name: "コーヒー", price: 170, stock: 8 },
            { id: 8, name: "紅茶", price: 140, stock: 6 }
        ];

        // 商品用のクラス定義
        class Item {
            static number = 1;
            constructor(name, price, stock) {
                this.id = Item.number;
                this.name = name;
                this.price = price;
                this.stock = stock;
                Item.number++;
            }

            // 商品一覧の表示関数
            static showItemList(list) {
                console.log("商品は以下の" + (list.length) + "種類です。");
                list.forEach(item => {
                    console.log(`商品番号: ${item.id}, 商品名: ${item.name}, 金額: ${item.price}, 在庫数: ${item.stock}`);
                });
                console.log(""); // 空行の出力
            }
            
            // 商品購入の関数
            buyItem() {          
                if (this.stock >= 1) { 
                    console.log("商品番号: "+this.id+", 商品名: "+this.name+"を購入します。");
                    this.stock--; // 購入による商品の在庫削減処理
                    console.log("残りは" + this.stock + "個です。");
                } else {
                    console.log(this.name+"は商品の在庫がないため購入できません。");
                }
            }
        } // End of Item class

        // 商品テーブルのエレメント抽出
        const itemArea = document.getElementById("item_area");
        itemArea.innerHTML += "<tr><th>商品名</th><th>金額</th><th>在庫数</th><th>購入</th></tr>";

        // 配列のオブジェクト作成
        const item_list = items.map(item => new Item(item.name, item.price, item.stock));
        
        // 商品表の作成
        item_list.forEach(item => {
            itemArea.innerHTML += `<tr>
                <td>${item.name}</td>
                <td>${item.price}円</td>
                <td>${item.stock}個</td>
                <td><button id="button${item.id}">購入</button></td>
            </tr>`;
        });

        // クリックイベント時の購入処理の設定
        for (let i = 0; i < item_list.length; i++) {
            document.getElementById("button" + item_list[i].id).onclick = () => {
                item_list[i].buyItem();
            };
        }

        Item.showItemList(item_list);
    </script>
</body>
</html>」
* コメント「課題4-1. ここにコードを書く」の箇所にコードを書くこと。
  

### 課題4-2．以下の要件を満たすように kadai4.html を修正せよ。
* kadai4-2.pngを参考に、商品名、金額、在庫数、購入ボタンが表示されるように修正せよ。
* tableタグを使って表を整形すること。
* コメント「課題4-2. ここにコードを書く」の箇所にコードを書くこと。
* 「課題４－２,
* <!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="utf-8">
  <title>演習課題4：自動販売機（クラス）</title>
  <style>
    table { border-collapse: collapse; }
    th, td { padding: .4em .8em; text-align: center; }
    th { background: #f0f0f0; }
  </style>
</head>
<body>
  <h1 id="vending-machine">自動販売機システム</h1>

  <table id="item_area" border="1">
    <tr><th>商品名</th><th>金額</th><th>在庫数</th><th>購入</th></tr>
  </table>

  <script>
    const items = [
      { id: 1, name: "緑茶",          price: 140, stock: 5  },
      { id: 2, name: "水",            price: 100, stock: 14 },
      { id: 3, name: "オレンジジュース", price: 150, stock: 7  },
      { id: 4, name: "リンゴジュース",  price: 150, stock: 9  },
      { id: 5, name: "炭酸水",        price: 120, stock: 1  },
      { id: 6, name: "サイダー",      price: 160, stock: 3  },
      { id: 7, name: "コーヒー",      price: 170, stock: 8  },
      { id: 8, name: "紅茶",          price: 140, stock: 6  }
    ];


    class Item {
      static number = 1;               // 次の id 割当用
      constructor(name, price, stock) {
        this.id    = Item.number++;
        this.name  = name;
        this.price = price;
        this.stock = stock;
      }

      static showItemList(list) {
        for (const it of list) {
          console.log(`id: ${it.id}, name: ${it.name}, ${it.price}円, 残り${it.stock}個`);
        }
        console.log(`商品は以下の${list.length}種類です。`);
      }

      buyItem() {
        if (this.stock >= 1) {
          console.log(`商品番号: ${this.id}, 商品名: ${this.name}を購入します。`);
          this.stock--;                                            // 在庫を 1 減らす
          console.log(`残りは${this.stock}個です。`);

          document.getElementById(`stock${this.id}`).textContent = this.stock;
        } else {
          console.log(`${this.name}は商品の在庫がないため購入できません。`);
        }
      }
    }

    const itemArea = document.getElementById("item_area");

    const item_list = items.map(obj => new Item(obj.name, obj.price, obj.stock));

    for (const it of item_list) {
      itemArea.insertAdjacentHTML(
        "beforeend",
        `<tr>
           <td>${it.name}</td>
           <td>${it.price}</td>
           <td id="stock${it.id}">${it.stock}</td>
           <td><button id="button${it.id}">購入</button></td>
         </tr>`
      );
    }

    for (const it of item_list) {
      document.getElementById(`button${it.id}`).onclick = () => it.buyItem();
    }

    Item.showItemList(item_list);
  </script>
</body>
</html>

### 課題4-3．以下の要件を満たすように kadai4.html を修正せよ。
* kadai4-3.pngを参考に、購入ボタンをクリックすると、商品表の在庫が減少するように修正せよ。
* コメント「課題4-3. ここにコードを書く」の箇所にコードを書くこと。

### 課題4-4．kadai4-4.md を修正して、Q4-1～4-3に解答せよ。
* マークダウン記法で記述すること。

### 課題4-5【オプション】．以下の要件を満たすように kadai4.html を改良せよ。
* 所持金の変数を用意して、商品購入の度にその金額が財布から引かれるように修正せよ。
* 所持金が不足している場合は、商品を購入できないように修正せよ。
* 所持金をページに表示し、購入時に「○○を購入しました。残金は～～円です。」と表示されるよう修正せよ。

### 課題提出方法
* 随時、作業内容をコミットして、自分の課題リポジトリに履歴を残すこと。
* 上記の課題が完成したら、プルリクエストを使って提出すること。
* 教員、TA/SAが確認したらフィードバックする。
