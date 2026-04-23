🧠 PromptFlow Builder

Biến ý tưởng → SPEC → CONTRACT → REVIEW_CONTRACT → TEST → IMPLEMENT → REVIEW → FIX
Tất cả trong 1 workflow có cấu trúc, không còn chat lung tung.

🚀 Overview

PromptFlow Builder là một web app (1 file HTML) giúp bạn:

Chuẩn hóa cách làm việc với AI
Không còn mất context giữa các phiên chat
Tái sử dụng prompt theo template
Build feature theo quy trình rõ ràng như “bản vẽ thi công”

👉 Từ “vibe code” → “controlled system”

⚙️ Tech Stack
🧩 HTML + CSS + Vanilla JS (no framework)
☁️ Supabase (database + realtime sync)
🧠 AI (ChatGPT / Claude / Gemini / Groq - dùng ngoài)
🏗️ Core Workflow
Idea
→ SPEC
→ CONTRACT
→ REVIEW_CONTRACT
→ TEST
→ IMPLEMENT
→ REVIEW
→ FIX

Mỗi bước:

có template sẵn
chỉ cần điền nội dung
copy sang AI để xử lý
🧠 Key Features
🧩 1. Prompt Template System
SPEC template
CONTRACT template
TEST template
IMPLEMENT template
REVIEW template
FIX template

👉 Không cần viết lại prompt mỗi lần

📦 2. Feature Library
Tạo nhiều feature riêng biệt
Mỗi feature có full workflow riêng
Thêm / sửa / xóa linh hoạt
💾 3. Local-first + Cloud Sync
Lưu local (localStorage)
Sync realtime qua Supabase
Mở nhiều thiết bị → update ngay
🔄 4. Realtime Sync
PC ↔ điện thoại
Tab ↔ tab
Không cần refresh
🌗 5. Dark / Light Mode
Toggle trực tiếp
Lưu trạng thái
📤 6. Import / Export JSON
Backup dữ liệu
Di chuyển giữa project
⚙️ 7. Config System
Sửa template trực tiếp trong app
Không cần đụng code
🧱 Database (Supabase)

Table: promptflow_data

Field Type
id uuid
user_id text
app_id text
data jsonb
updated_at timestamp

👉 Unique:

(user_id, app_id)
🔧 Setup

1. Clone repo
   git clone https://github.com/your-username/promptflow-builder.git
   cd promptflow-builder
2. Mở file

Chỉ cần mở:

index.html

👉 chạy luôn, không cần build

3. Setup Supabase
   Tạo project trên Supabase
   Chạy SQL:
   create extension if not exists "pgcrypto";

create table promptflow_data (
id uuid primary key default gen_random_uuid(),
user_id text not null,
app_id text not null,
data jsonb not null default '{}'::jsonb,
updated_at timestamp with time zone default now(),
constraint unique_user_app unique (user_id, app_id)
); 4. Thêm config vào code

Trong index.html:

const SUPABASE_URL = "YOUR_URL";
const SUPABASE_ANON_KEY = "YOUR_KEY";

const USER_ID = "RongLeo";
const APP_ID = "PromptFlow-Builder";
🌐 Deploy
Deploy lên Vercel
Push repo lên GitHub
Vào https://vercel.com
Import project
Deploy

👉 Xong, web chạy online

⚠️ Lưu ý
App không có backend riêng
Supabase dùng anon key (client-side)
Hiện tại:
overwrite data (last write wins)
chưa có conflict resolver
🧠 Design Philosophy
Không build AI → build cách làm việc với AI
Không chat → structured thinking
Không phụ thuộc 1 model → model-agnostic
🔮 Future Ideas
🔐 Auth (multi-user)
🕰️ Version history (time travel)
⚔️ Conflict resolver
📊 Dashboard analytics
🤖 Auto AI execution (optional)
🎯 Use Case
Solo builder
Vibe coder
Product thinker
Người không phải dev nhưng muốn build tool
🤝 Contributing

Hiện tại project dùng cho cá nhân.
Nếu muốn mở rộng → fork và tùy biến.

📜 License

MIT

🧠 Final Thought

AI không làm thay bạn
nhưng nếu có hệ thống tốt
nó sẽ trở thành đội dev của bạn
