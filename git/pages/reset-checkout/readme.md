# `checkout` и `reset`

<br>

## 🚩 Команда `checkout`
`git checkout` используется для перемещения между ветками, коммитами и тегами. Она также позволяет восстанавливать файлы из определенных коммитов или веток.

### Использование
  <details>
   <summary>🔹 Переключение между ветками:</summary>
    
  <br>
      
  ```sh
  git checkout <branch_name>
  ```
  </details>
  <br>
  <details>
   <summary>🔹 Переключение на определенный коммит:</summary>
       
  <br>
      
  ```sh
  git checkout <commit_hash>
  ```
  👆 `HEAD` будет указывать не на ветку, а на конкретный коммит
  
  </details>
   <br>
  <details>
   <summary>🔹 Восстановление файла из определенного коммита:</summary>
    
  <br>
      
   ```sh
   git checkout <commit_hash> -- <file_path>
   ```
  </details>
  <br>
  <details>
    <summary>🔹 Создание новой ветки и переключение на нее:</summary>
        
  <br>
      
   ```sh
   git checkout -b <new_branch_name>
   ```
  </details>

### Важно ❗
Флаг `-f` для принудительного переключения ветки и сброса всех несохраненных изменений в рабочем каталоге и индексе..

<br>
<br>

## 🚩 Команда `reset`
`git reset` используется для изменения состояния индекса и рабочего каталога. Она позволяет отменять коммиты, изменять состояние коммитов и перемещать ветки.

### Использование
  <details>
    <summary>🔹 Отмена коммита с сохранением изменений в рабочем каталоге:</summary>

   ```sh
   git reset --soft <commit_hash>
   ```
  </details>

  <details>
    <summary>🔹 Отмена коммита с сбросом изменений в индексе:</summary>

   ```sh
   git reset --mixed <commit_hash>
   ```
  </details>

  <details>
    <summary>🔹 Отмена коммита с полным удалением изменений:</summary>

   ```sh
   git reset --hard <commit_hash>
   ```
  </details>

  <details>
    <summary>🔹 Сброс индекса до определенного состояния:</summary>

   ```sh
   git reset <commit_hash>
   ```
  </details>


<br>
<br>

## Отличия 🛑

### Изменение состояния: 
&emsp;🔵 `git reset` изменяет состояние индекса и HEAD, а `git checkout` меняет состояние HEAD и файлов в рабочем каталоге

### История коммитов: 
&emsp;🔵 `git reset` может изменять историю коммитов, в то время как `git checkout` - нет.

### Создание веток: 
&emsp;🔵 `git checkout` может создавать новые ветки и переключаться на них, чего не может `git reset`.

### Восстановление файлов: 
&emsp;🔵 `git checkout` используется для восстановления файлов из определенных коммитов.
