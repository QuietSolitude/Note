# 使用GitHub进行工作的流程    
  一般我们在开发的时候都是分布式的，各自完成ticket。然后将完成的ticket push到项目里，但是最好是push在分支。方便检查ticket是否符合完成    
  条件。    

创建分支和push分支    
---------------------------------------
  分支应该在库里面创建    
  1. 先根据ticket的内容来定义分支的名称。比如issue-1    
  2. 使用`git checkout -b 分支名称`来创建一个分支。    
  3. 使用`git status`检查当前是否在这个分支上。 
  4. 当完成ticket后，要将代码push到分支上。    
    - `git add . //添加所有的文件到git上`
    - `commit -m"xxxx" //对add内容进行注释`
    - `git push origin 分支名 //将内容push在分支上`
  5. push完后，回到工程的GitHub上找到Pull requests,点击一下。    
    - [pull requests](images/Pull_Requests.jpeg)
  6. 然后点击右上面的compare&pull requests
    - [compare](images/compare_Pull_Request.jpeg)
  7. 在title里面添加信息。例如Added playbook to update the HTTPS certificate.
    - [title](images/Title_Message.jpeg)
  8. 在Preview里填写ticket完成后的信息。 
    - [preview](images/Preview.jpeg)
  9. 然后点击create pull request. 
  10. 完成后在ticket上的preview里填写信息，确认无误之后点击comment。
    - [ticket](images/Ticket_Preview.jpeg)    
  11. 然后将ticket移动到in review上检查代码是否写得对。
    - [inReview](images/In_Review.png)
  12. 检查无误之后，将ticket移动到Done里。