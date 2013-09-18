Average
=======
if( !class_exists('MMMR_CLASS') ){

  class MMMR_CLASS{

      public static _MMMR($array=array(), $output = 'mean'){
          if(!is_array($array)){
              return FALSE;
          }else{
              switch($output){
                  case 'mean':
                      $count = count($array);
                      $sum = array_sum($array);
                      $total = $sum / $count;
                  break;
                  case 'median':
                      rsort($array);
                      $middle = round(count($array) / 2);
                      $total = $array[$middle-1];
                  break;
                  case 'mode':
                      $v = array_count_values($array);
                      arsort($v);
                      foreach($v as $k => $v){$total = $k; break;}
                  break;
                  case 'range':
                      sort($array);
                      $sml = $array[0];
                      rsort($array);
                      $lrg = $array[0];
                      $total = $lrg - $sml;
                  break;
              }
              return $total;
          }
      }

  }

}

$arr = array(12,33,23,4,20,124,4,2);

// Mean = The average of all the numbers
echo 'Mean: '.MMMR_CLASS::MMMR($arr).'<br>';
echo 'Mean: '.MMMR_CLASS::MMMR($arr, 'mean').'<br>';

// Median = The middle value after the numbers are sorted smallest to largest
echo 'Median: '.MMMR_CLASS::MMMR($arr, 'median').'<br>';

// Mode = The number that is in the array the most times
echo 'Mode: '.MMMR_CLASS::MMMR($arr, 'mode').'<br>';

// Range = The difference between the highest number and the lowest number
echo 'Range: '.MMMR_CLASS::MMMR($arr, 'range');
