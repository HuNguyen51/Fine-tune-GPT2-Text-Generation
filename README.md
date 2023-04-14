# Fine-tune-GPT2-Text-Generation là một bài tự sinh văn bản sử dụng GPT với dữ liệu <a href='https://github.com/NTT123/viwik18/tree/viwik19'>wiki-vi19</a>
## Giới thiệu
- Đây là bài toán tự sinh văn bản khi cho 1 chuỗi văn bản đầu vào và nó sẽ sinh ra n các từ tiếp theo
- Về dữ liệu: mình lấy dữ liệu wiki-vi19 - là bộ dữ liệu được crawl về từ wikipedia, đây cũng là bộ data dành cho việc sinh từ trong tiếng Việt
- Về model: mình sử dụng model GPT pre-train của NlpHust, GPT là model sinh từ cũng như làm chatbot với độ hiệu quả rất cao và rất thông minh
## Xử lý dữ liệu
- Khi tải file zip từ link trên về và giải nén ta sẽ có một thư mục dataset, trong thư mục dataset sẽ có những thư mục con chứa các đoạn văn bản
dataset:
  wiki1  
  wiki2  
- Từ các file dữ liệu text đó mình sẽ đọc hết tất cả (có thể xử lý sạch sẽ ở đây để khi đọc ra ta không cần xử lý nhiều nữa) và gom lại thành 1 file lớn duy nhất để khi train mình chỉ cần đọc 1 file
- Sau khi đọc và gom dữ liệu mình ghi nó vào file data.txt  
LƯU Ý: trong bài này dữ liệu có sao thì mình để vậy và không xử lý gì cả, không bỏ ký tự đặc biệt, không viết thường,...
## Chi tiết model
- Đây là model GPT train sẵn dành cho tiếng Việt của <a href='https://huggingface.co/NlpHUST/gpt2-vietnamese'>NlpHUST/gpt2-vietnamese</a> được train dựa trên causal language modeling (CLM) được giới thiệu trên <a href='https://openai.com/research/better-language-models'>trang này</a>
- Kiến trúc của model có 12 layers và 768 hidden size
- Theo như NlpHust - Mô hình này đã được đào tạo trên bộ dữ liệu Oscar tiếng Việt (32 GB) để tối ưu hóa mục tiêu mô hình hóa ngôn ngữ truyền thống trên TPU v3-8 trong khoảng 6 ngày.
- Và chúng ta sẽ sử dụng nó để fine-tune lại dùng cho mục đích của mình trên bộ dữ liệu cá nhân
