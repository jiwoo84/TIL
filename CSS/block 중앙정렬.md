# 1/28 block 중앙정렬

## **여러 블럭 한줄로 맞추기**

space-between 상태

하지만 시계가 정가운데 아니고 가지고 있는 높이가 달라서 들쑥날쑥 이럴때 사용할 css hack

1. 먼저 space-between → center

`부모 {justify-content:center;}`

1. 각자 같은 값의 width 부여 (3개니까 33%로)
    
    `자식 width: 33%;`
    
2. 가운데 부분을 flex/ center
    
    `display: flex;`
    
    `justify-content: center;`
    
    or
    
    (text면) `text-align: center;`
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/012fa906-1deb-43ce-83ea-f0fb805c86df.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/012fa906-1deb-43ce-83ea-f0fb805c86df.png)
    
3. 나머지 flex 주고 원하는대로 조정
4. margin 정리 필요하다면
    
    (왼) margin-right: auto;
    
    (오) margin-left: auto;