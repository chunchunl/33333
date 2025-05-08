筆記內容
note_content = """\
GitHub 多人協作全流程筆記（寶寶版）
一、初始化專案並上傳 GitHub
mkdir museum-project
cd museum-project
git init
git add .
git commit -m "Initial commit"


建立 GitHub Repo（不要勾選 Initialize README）
git remote add origin https://github.com/babe/museum-project.git
git branch -M main
git push -u origin main


---

二、建立 dev 分支作為開發主線
git checkout -b dev
git push -u origin dev


---

三、團隊成員加入專案 & 各自開發
Clone 專案並切到 dev
git clone https://github.com/babe/museum-project.git
cd museum-project
git checkout dev


從 dev 分支開新功能分支
git checkout -b feature/功能名稱
git push -u origin feature/功能名稱


---

四、開發 → 合併到 dev 分支
確保分支是最新（避免 conflict）
git checkout feature/功能
git pull origin dev --rebase


合併功能分支到 dev
git checkout dev
git merge feature/功能
git push origin dev


---

五、PM 將 dev 合併到 main（準備發佈）
git checkout main
git pull origin main
git merge dev
git push origin main


---

六、打版本 Tag（可回溯）
git tag v1.0.0
git push origin v1.0.0


---

分支結構示意
main        ← 正式發佈線
└── dev     ← 團隊共用開發線
    ├── feature/login
    ├── feature/chat
    ├── fix/email-bug


---

常用 Git 指令整理
git branch -a                           # 查看所有分支
git checkout -b dev origin/dev         # 拉取遠端 dev
git log --oneline --graph --all        # 查看 commit 圖表
git merge feature/xxx                  # 合併分支
git branch -d feature/xxx              # 刪除本地分支
git push origin --delete feature/xxx   # 刪除遠端分支

"""

儲存為筆記檔案
note_path = Path("/mnt/data/github-collaboration-note.md")
note_path.write_text(note_content, encoding="utf-8")

note_path.name
