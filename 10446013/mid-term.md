## 說明

1. 答案直接寫在這個 `mid-term.md` 裡，並使用 Markdown 語法撰寫。
1. 題目總共分 Ruby、Rails 以及 Git 三大主題，請在每個主題完成時進行 Commit。
1. 完成後，請發送 PR 至 `mid-term` 分支。
1. 也就是說，你的 PR 應該只會有三或四次的 Commit。

## Ruby 題目 (50 分)

1. (10 分) 請完成本題實作內容

```ruby
class Cat
  def initialize(name)
    @name = name
  end
  
  def name
    @name
  end
end

kitty = Cat.new("kitty")
puts kitty.name  # 在畫面上印出 kitty 字樣
```

2. (5 分) 假設有個 Hash：

```ruby
profile = {name: "kk", age: 18}
```

當執行這行程式：

```ruby
p profile["name"]
```

會得到什麼結果? 為什麼?<br><br>
ans: 得到nil，因為陣列裡沒有"name"(字串)這個東西，要顯示"kk"的話，要改成p profile[:name]<br>

3. (5 分) 如果要在 1 到 100 的數字當中，任意取出 5 個不重複的亂數，你會怎麼做？
```
puts [*1..100].sample(5)
```

4. (10 分)
```ruby
class Bank
  def transfer(amount)
    # ...
  end
end

Bank.transfer(10)
```

上面這段程式碼執行後會發生什麼事？為什麼？如果有錯誤又該如何修正？<br><br>
ans:出現方法未定義，因為ruby 沒有類別方法，但能透過singleton method的方式，此處錯誤修正方法：transfer --> self.transfer

5. (10 分) 請問以下方法：

```ruby
link_to "刪除", products_path(product), method: :delete, class: "btn btn-default"
```

`link_to` 方法共有幾個參數？為什麼？
ans: 三個參數，分別為[名稱]、[路徑]、[html設定(方法、class等)]，method、class被包一起視為一個參數，所以位置交換也沒關係，此方法原寫成：<br>
```
link_to ("刪除", products_path(product), {method: :delete, class: "btn btn-default"})
```
6. (10 分) 在 Ruby 裡面常會看到冒號的寫法，例如：

有的冒號靠右邊：

```ruby
class Store
  has_many :products
end
```

有的冒號靠左邊：

```ruby
link_to "檢視", books_path(book), class: "btn btn-default"
```

或是兩邊都有：

```ruby
user_profile = {name: "kk", age: 18, blood_type: :b_negative}
```

請問，這三種寫法分別代表什麼意思呢？<br>
ans:<br>
1. :products代表的是此為一個符號，跟普通變數很像，但卻是不可變更的。<br>
2. class: "btn btn-default"，這邊則為一般用法，將class設定為btn btn-default樣式。<br>
3. user_profile = {name: "kk", age: 18, blood_type: :b_negative}，使用兩個冒號表示要要將blood_type設定為:b_negative，但b_negative是一個不可變更的符號。

## Rails 題目 (30 分)

1. (10 分) 請簡述 `bundle install` 指令的用途。<br>
ans: bundle install，自動下載並安裝要開啟的rails專案所需要的gemfile。

2. (10 分) 請說明 `rails db:migrate` 這個指令的用途是什麼？<br>
ans: rails db:migrate，執行將剛才migration出來的資料進行寫入當前資料庫的動作。

3. (10 分) 假設某個 Controller 的程式碼如下：

```ruby
class BooksController < ApplicationController
  def index
    @books = Book.all
  end

  def update
    @book = Book.find_by(id: params[:id])
    @book.update(price: 100)
    redirect_to books_path, notice: "資料更新成功"
  end
end
```

請問：
- 第 3 行的 `@books` 前面的那個 `@` 是什麼意思？如果把 `@` 拿掉會發生什麼事？
- 第 7 行以及第 8 行的 `@book`，如果把 `@` 拿掉會發生什麼事？為什麼？<br><br>
ans:<br>
1. @books的@是為了讓books變成instance variable ，讓他可以在不同方法間使用。<br>
2. 在此段程式碼中不會出現錯誤，因為只是將值塞進book變數中，就算不使用instance variable也不會影響，但整個rails執行時，會因為找不到@book變數導致發生錯誤。

## Git 題目 (20 分)

1. (10 分) 在你想像中的分支(branch)，是個什麼樣子的東西?

1. (5 分) 空的資料夾無法被加入 Git 版控，但如果就是想讓這個資料夾留下來，你會怎麼處理?

2. (5 分) 如果有些檔案，像是 `/config/database.yml` 之類比較機密的檔案，不想放在 Git 裡面，你會怎麼做？

