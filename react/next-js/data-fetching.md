# Data Fetching
Tài liệu chi tiết tại đây [Data Fetching](https://nextjs.org/docs/basic-features/data-fetching/overview)

- getServerSideProps
- getStaticProps
- getStaticPaths
- Incremental Static Regeneration
- Client side

Chú ý: getServerSideProps sẽ có thể làm giảm tốc độ, trải nghiệm người dùng và luôn đòi hỏi phải pre-render mỗi khi gọi.

Hoàn toàn có thể sử dụng useEffect để thay thế việc load data.

