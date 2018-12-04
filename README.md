# Simple PHP Script for Google News
Simple and easy PHP Script to get the news from Google news for a spacial keyword. 

```php
$google_news_API="YOUR API HERE";
$search_keyword="Apple in India"; 
$news_count=1; //Set the News result count
$days_ago = date('Y-m-d', strtotime('-2 days')); //Set date for past news
$search_keyword=str_replace(" ","+",$search_keyword);
$json_response=file_get_contents("https://newsapi.org/v2/everything?q=".$search_keyword."&from=".$days_ago."&sortBy=date&apiKey=".$google_news_API);
$json_array=json_decode($json_response,true);
$nos_of_post=0;
$news_count=$news_count*5;
$news=array();
foreach($json_array as $ja)
{
  if(is_array($ja)){
  foreach($ja as $response)
  {     
                  if(is_array($response)){
                          foreach($response as $res)
                          {
                              if(!is_array(($res)))
                              {
                              if($nos_of_post==$news_count) break;
                               array_push($news,$res);
                              $nos_of_post++;
                              }                           
                              
                          }
                 }     
         }
     } 
}
var_dump($news);
```
