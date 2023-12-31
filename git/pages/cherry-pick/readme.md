# `cherry-pick`
> Скопировать указанный комит из другой ветки в указанную ветку

<br>

## Использование

  <details>
  <summary> 🔹 Скопировать указанный коммит</summary>
  <br>
  🚩 Создает новый коммит с теми же изменениями, что и выбранный коммит
    
  <br>
  <br>
    
  🚩 Новые коммиты имеют новые идентификаторы, так как они отличаются от оригинальных коммитов в истории

  <br>
  
  ```bash
  git cherry-pick <commit_hash>.
  ```
  </details>
  
  <br>
  
  <details>
  <summary> 🔹 Скопировать все комиты отстутствующие в HEAD из указанной ветки</summary>
  <br>
  🚩 Флаг `-n` подтянет изменения в рабочую директорию, но без коммита
    
  <br>

  <br>
  
  ```bash
  git cherry-pick master..feature
  ```

  👆 Скопировать все комиты из feature, которых нет в master
  </details>

  <br>

  ## Отмена

  ```bash
  git cherry-pick --abort
  ```
