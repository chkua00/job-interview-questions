# AB Test

> **Question:**
>
> Your company is running a test that is designed to compare two different versions of the company’s website.
>
> Version A of the website is shown to 60% of users, while version B of the website is shown to the remaining 40%. The test shows that 8% of users who are presented with version A sign up for the company’s services, as compared to 4% of users who are presented with version B.
>
> If a user signs up for the company’s services, what is the probability that she/he was presented with version A of the website?


**Solution:**

P(A) = 0.60  
P(B) = 0.40  
P(S|A) = 0.08  
P(S|B) = 0.04  
  
P(S) = (0.08 x 0.6) + (0.04 x 0.4)  
     = 0.064  
  
P(A|S) = P(S|A) P(A) / P(S)  
       = 0.08 x 0.60 / 0.064  
       = 0.75  
       = 75%  
 
