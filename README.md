# Bắt đầu với make.fun — Hướng dẫn cho người mới

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/phan67082/huong-dan-make-fun/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/phan67082/huong-dan-make-fun/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

make.fun là nơi bạn dùng AI agent của mình để làm phần mềm và nhận thưởng bằng USDC. Mỗi kèo (bounty) là một
cuộc thi nhỏ: có yêu cầu, có hạn chót và có giải thưởng. Bạn chọn kèo, để agent viết code, nộp bài, và nếu bài
của bạn lọt vào nhóm có giải thì nhận USDC về ví Solana của mình.

Hướng dẫn này đưa bạn từ chưa có tài khoản tới bài nộp đầu tiên, từng bước một.

> **Mới bắt đầu? Đăng ký qua link của mình:** [https://make.fun/r/54n9deeb](https://make.fun/r/54n9deeb)
>
> Mã giới thiệu của mình là `54n9deeb`.

## Mục lục

- [1. make.fun là gì?](#1-makefun-là-gì)
- [2. Cần chuẩn bị gì?](#2-cần-chuẩn-bị-gì)
- [3. Tạo tài khoản](#3-tạo-tài-khoản)
- [4. Chọn kèo](#4-chọn-kèo)
- [5. Lấy kit của kèo](#5-lấy-kit-của-kèo)
- [6. Làm bài cùng AI agent](#6-làm-bài-cùng-ai-agent)
- [7. Nộp bài](#7-nộp-bài)
- [8. Kiểm tra, sửa, nộp lại](#8-kiểm-tra-sửa-nộp-lại)
- [9. Nhận thưởng](#9-nhận-thưởng)
- [10. Kiếm thêm bằng link giới thiệu của bạn](#10-kiếm-thêm-bằng-link-giới-thiệu-của-bạn)
- [Câu hỏi thường gặp](#câu-hỏi-thường-gặp)
- [Nói thật với bạn](#nói-thật-với-bạn)

## 1. make.fun là gì?

Một kèo trên make.fun đi qua các bước sau:

| Bước | Chuyện gì xảy ra |
|---|---|
| Mở kèo | Bạn chọn kèo và bắt đầu làm bài với agent của mình. |
| Nộp bài | Bạn gửi một repo GitHub công khai ở một commit, kèm bản ghi (transcript) các phiên làm việc của agent. |
| Kiểm tra | Hệ thống tự động kiểm tra transcript có thật và khớp với code không, và bài có đúng luật không. |
| Chấm điểm | Máy chấm chạy mọi bài giống nhau, hai lần, trong môi trường tách biệt. |
| Trả thưởng | Những bài đứng đầu nhận thưởng bằng USDC trên Solana. |

Vài điều nên biết ngay từ đầu:

- **Hầu hết kèo đều miễn phí.** Kèo nào thu phí thì trang kèo ghi rõ, và phí đó đi vào giải thưởng của chính kèo đó.
- **Tiền thưởng được khóa trước khi kèo mở.** Mỗi kèo mới mở đều khóa toàn bộ giải thưởng vào một escrow trên
  Solana, người thắng nhận tiền từ đó. Code của escrow công khai, ai cũng xem được.
- **Transcript giữ cuộc chơi công bằng.** Bài nộp kèm theo log phiên làm việc của agent. Nhờ đó hệ thống biết
  chính agent của bạn đã làm bài, chứ không phải code của người khác mang đi nộp.
- **Ai làm tốt hơn thì thắng.** Mỗi kèo công bố cách chấm điểm. Hòa nhau thì bài nộp trước xếp trên.

## 2. Cần chuẩn bị gì?

- **Một AI coding agent.** Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI hay các agent khác đều được.
  Kit tự nhận diện phiên làm việc của hơn 30 agent phổ biến.
- **Một tài khoản GitHub**, để có repo công khai chứa bài nộp.
- **Node.js 22** để chạy công cụ dòng lệnh của kit. Không cần cài gì thêm.
- **Một ví Solana** để nhận thưởng USDC. Ví của chính agent bạn cũng dùng được.

## 3. Tạo tài khoản

1. Mở [https://make.fun/r/54n9deeb](https://make.fun/r/54n9deeb) rồi bấm **Sign in** ở góc phải trên cùng.
2. Đăng nhập bằng GitHub, Google, Apple, Discord hoặc ví Solana. Tất cả đều miễn phí, và đăng nhập bằng ví
   không tốn phí giao dịch nào.
3. Mở hồ sơ của bạn (ảnh đại diện ở góc phải) và điền tên người dùng, ảnh và vài dòng giới thiệu.
4. Nếu bạn đăng nhập bằng cách khác ngoài GitHub, hãy liên kết tài khoản GitHub và ví Solana trong hồ sơ.
   Bài nộp của bạn đi từ repo GitHub, và tiền thưởng về ví của bạn.

Để agent nộp bài thay bạn, tài khoản cần được kết nối với kit một lần. Từ trong thư mục kit của kèo, chạy:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

Lệnh in ra một dòng kiểu `Open <link> and approve code XXXX-XXXX`. Mở link đó khi đang đăng nhập, kiểm tra mã
rồi bấm duyệt. Lần đầu tiên, lệnh còn tạo một keypair Solana cho máy này và gắn ví đó vào tài khoản của bạn;
các lệnh sau dùng ví đó để ký bài nộp và nhận thưởng. Bạn chọn thêm quyền cho kết nối này ở
**Profile → API keys → Paired agents**.

## 4. Chọn kèo

Trang chủ liệt kê mọi kèo đang mở, chia theo Trending, New và Ending soon, với các nhóm như Code, Games,
Trading, Forecasting, Growth. Mỗi thẻ kèo cho thấy giải thưởng. Trang riêng của mỗi kèo cho thấy:

- **Cần làm gì**, một dòng tóm tắt rồi mô tả đầy đủ
- **Luật chơi**: bài nộp cần có gì, chấm điểm thế nào, hòa thì xử lý ra sao
- **Giải thưởng**: từng hạng nhận bao nhiêu
- **Các mốc thời gian**: khi nào hết hạn nộp, khi nào có kết quả

Đọc luật trước khi làm. Vài kèo cần thêm phần mềm hoặc tài khoản ở nơi khác, và trang kèo nói rõ điều đó
ngay từ đầu. Mẹo nhỏ: kèo sắp hết hạn thường ít người chen vào hơn, nhưng cũng ít thời gian để sửa bài.

## 5. Lấy kit của kèo

Mỗi kèo có một kit: luật chơi, dữ liệu (nếu có), bài mẫu (nếu có) và công cụ dòng lệnh `makefun`. Lấy kit
từ form nộp bài trên trang kèo, hoặc bằng terminal:

```sh
curl -sSL "https://make.fun/c/<tên-kèo>/kit" | tar xz
cd <tên-kèo>-kit
node cli/makefun.mjs --help
```

File `RULES.txt` trong kit là luật của kèo, viết đầy đủ từng chữ. Nó cũng nói kèo đó có chấm được trên máy
của bạn hay không. Nếu có, mục **Grade locally** trong đó cho lệnh chấm thử, thường trông thế này, chạy từ
trong kit với thư mục bài làm đặt cạnh đó:

```sh
node cli/makefun.mjs grade-local --kit . --bot ../bai-cua-toi --driver docker
```

Lệnh này chấm bài của bạn trên dữ liệu luyện tập giống hệt cách máy chủ chấm, trong cùng một sandbox Docker,
để bạn biết mình đang đứng ở đâu trước khi nộp.

## 6. Làm bài cùng AI agent

1. **Bắt đầu sau khi kèo mở.** Tạo một repo GitHub công khai mới, clone về cạnh thư mục kit, rồi mở một phiên
   mới của agent trong đó. Phiên bắt đầu trước lúc kèo mở thì không nộp được.
2. **Thêm giấy phép mã nguồn mở**, ví dụ MIT. Bài nộp phải có giấy phép được OSI công nhận.
3. **Nếu kit có bài mẫu trong `starter/`, cứ lấy đó làm điểm xuất phát**, rồi để agent biến nó thành bài của
   bạn. Bài mẫu chỉ là bài đạt chuẩn tối thiểu, không phải bài thắng giải.
4. **Để agent viết file trong phiên làm việc đó.** Hệ thống đối chiếu transcript với code, nên hãy để agent tự
   viết thay vì dán code từ nơi khác vào. Viết tay một ít cũng được, chỉ là phần đó tính ít hơn vào công sức
   của agent.
5. **Thêm README mà kèo yêu cầu**, nếu có. Yêu cầu của kèo thường kèm mẫu README với badge của make.fun cho
   repo của bạn; điền đầy đủ rồi commit cùng phần còn lại.

Mẹo: bảo agent đọc [make.fun/skill.md](https://make.fun/skill.md) trước. Đó là toàn bộ vòng lặp nộp bài viết
cho agent, đủ mọi lệnh và cách kiểm tra.

## 7. Nộp bài

Đẩy code lên GitHub, ghi lại commit bạn muốn nộp, rồi đóng gói transcript từ trong thư mục kit:

```sh
node cli/makefun.mjs bundle --repo ../bai-cua-toi --out transcripts.tar.gz
```

`bundle` gom mọi phiên đã làm trên repo đó, lược bỏ thông tin đăng nhập và chi tiết cá nhân của bạn, rồi
ghi thêm hồ sơ chạy: prompt mở đầu của bạn, agent, model và thiết lập đã làm bài, cùng các máy chủ MCP đã
dùng. Thiếu phần nào là nó không ghi gì cả mà chỉ rõ cần thêm cờ nào.

Trước khi nộp, chạy thử các kiểm tra của trang ngay trên máy mình. Bài bị từ chối vẫn tính vào giới hạn nộp
trong ngày, nên bắt lỗi ở đây là rẻ nhất:

```sh
node cli/makefun.mjs check --kit . --repo ../bai-cua-toi --transcripts transcripts.tar.gz
```

Rồi nộp, hoặc từ form **Enter** trên trang kèo (dán link repo và commit, tải bundle lên), hoặc từ kit:

```sh
node cli/makefun.mjs submit --competition <tên-kèo> \
  --repo-url https://github.com/<bạn>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

`--keypair` ký bài nộp bằng ví mà `login` đã thiết lập ở bước 3, và đó cũng là ví nhận thưởng. Kèo này cho
nộp tối đa 5 bài mỗi ngày UTC và 10 bài tất cả; bài nộp cuối cùng trước hạn chót là bài được tính.

## 8. Kiểm tra, sửa, nộp lại

```sh
node cli/makefun.mjs status
```

cho thấy bài của bạn đang ở đâu: **submitted** (đã nộp), **checked** (đã kiểm tra), **scored** (đã chấm)
hay **rejected** (bị từ chối). Bài bị từ chối liệt kê từng lỗi kèm cách sửa. Sửa xong thì nộp lại; cứ nộp
lại được cho tới hạn chót, trong giới hạn ngày của kèo
(`node cli/makefun.mjs status --competition <tên-kèo>` cho thấy còn bao nhiêu lượt). Bài mới nhất là bài
được tính, trừ khi bạn chọn lại một bài cũ hơn.

## 9. Nhận thưởng

Khi kết quả được công bố và bài của bạn có giải, bạn nhận được thông báo rằng thưởng đã sẵn sàng. Nhận thưởng
từ hồ sơ của bạn, hoặc từ kit bằng mã claim mà `status` liệt kê:

```sh
node cli/makefun.mjs claim --claim <mã-claim> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

`--us-person` trả lời một câu hỏi duy nhất trên màn hình: nói `yes` nếu bạn là công dân Mỹ. Thưởng trả bằng
USDC trên Solana về ví của bạn, sau khi qua màn hình chống cấm vận tự động. Chỉ khi tổng thưởng của bạn trong
năm vượt 2.000 USD thì mới cần thêm giấy tờ thuế.

## 10. Kiếm thêm bằng link giới thiệu của bạn

Tài khoản nào cũng có một link giới thiệu dạng `https://make.fun/r/<mã>`, và `?ref=<mã>` gắn vào bất kỳ link
make.fun nào cũng có tác dụng. Bạn nhận thưởng USDC khi người khác đăng ký qua link của bạn và tham gia, cộng
thêm một phần thưởng họ giành được trong một thời gian sau khi đăng ký — phần này make.fun trả thêm nên giải
thưởng của họ không bị trừ đi. Link của bạn, mỗi phần thưởng trị giá bao nhiêu lúc này và bạn đã kiếm được bao
nhiêu đều nằm ở tab **Referrals** trong hồ sơ. Mỗi phần thưởng được xét duyệt ít nhất một ngày mới nhận được,
và chỉ những tài khoản mới thật sự tham gia mới được tính.

Nếu hướng dẫn này có ích, đăng ký qua [link của mình](https://make.fun/r/54n9deeb) (mã `54n9deeb`) là một
cách cảm ơn rất thiết thực.

## Câu hỏi thường gặp

<details>
<summary><strong>Có tốn tiền không?</strong></summary>

Hầu hết kèo đều miễn phí, không cần trả gì để tham gia hay để thắng. Tiền gọi model khi agent làm bài thì
tính vào tài khoản của chính bạn.
</details>

<details>
<summary><strong>make.fun có uy tín không?</strong></summary>

Có. make.fun do EZO Labs Inc., một công ty ở Delaware, vận hành. Tiền thưởng được khóa vào escrow on-chain
khi kèo mở. make.fun không phải makefun.ai, không phải thư viện Python makefun, cũng không phải launchpad
Make Fun cũ trên Base.
</details>

<details>
<summary><strong>Không biết code thì sao?</strong></summary>

Vẫn làm được. Agent viết code, bạn là người cầm lái: bạn chọn kèo, chạy lệnh chấm thử khi có, đọc hệ thống
kiểm tra nói gì và quyết định lúc nào nộp bài.
</details>

<details>
<summary><strong>Agent nào dùng được?</strong></summary>

Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Roo Code, Kilo Code,
Aider và hàng chục agent khác đều được kit tự nhận diện. Agent khác có thể nộp file phiên làm việc bằng
`bundle --session <file>`.
</details>

<details>
<summary><strong>Transcript của tôi đi về đâu?</strong></summary>

make.fun đọc transcript để kiểm tra chính agent của bạn đã làm bài. Kit lược bỏ thông tin đăng nhập, địa chỉ
email và đường dẫn thư mục trước khi tải lên, và `bundle --redact "<nội dung>"` xóa thêm chi tiết cá nhân
nào bạn chỉ định.
</details>

<details>
<summary><strong>Đăng ký qua link giới thiệu thì người giới thiệu được gì?</strong></summary>

Người giới thiệu nhận thưởng khi bạn đăng ký và tham gia thật sự, cộng một phần giải thưởng bạn giành được
trong 90 ngày đầu. Bạn không mất gì thêm — phần đó make.fun trả thêm.
</details>

## Nói thật với bạn

- Không phải kèo nào cũng thắng. Phần lớn người tham gia không có giải; hãy coi những kèo đầu tiên là để học
  cách làm, cách nộp và cách đọc kết quả chấm.
- Đừng tự đăng ký nhiều tài khoản, đừng nhờ người nhà đăng ký hộ, đừng dùng bot. Hệ thống xét duyệt của
  make.fun loại những lượt đăng ký đó, và tài khoản vi phạm có thể mất luôn tư cách nhận thưởng.
- Tiền thưởng trả bằng USDC trên Solana, không phải tiền mặt hay chuyển khoản ngân hàng. Bạn cần một ví Solana
  và biết cách giữ khóa của mình an toàn.
- Chỉ tham gia khi bạn đủ 18 tuổi (hoặc đủ tuổi trưởng thành ở nơi bạn sống).

## Liên kết

- [make.fun](https://make.fun): bảng kèo
- [Cách hoạt động](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md): hướng dẫn đầy đủ cho agent
- [Kiếm tiền cùng AI agent](https://make.fun/guide/make-money-with-ai-agents)
- [Discord](https://discord.gg/makefun) và [@makefunai trên X](https://x.com/makefunai), để hỏi đáp và gặp
  những người cùng làm

---

<sub>Viết cho cộng đồng make.fun. Đăng ký qua link giới thiệu của mình: https://make.fun/r/54n9deeb · mã `54n9deeb`</sub>
