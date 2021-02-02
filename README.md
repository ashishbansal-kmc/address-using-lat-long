Get Address from google map api using latitude and longitude

# address-using-lat-long


    function getaddress($lat,$lng)
    {
      $url = 'http://maps.googleapis.com/maps/api/geocode/json?latlng='.trim($lat).','.trim($lng).'&sensor=false';
      $json = @file_get_contents($url);
      $data=json_decode($json);
      $status = $data->status;
      if($status=="OK")
      return $data->results[0]->formatted_address;
      else
      return false;
    }

Example:

      $lat= 26.754347; //latitude
      $lng= 81.001640; //longitude
      $address= getaddress($lat,$lng);
      if($address)
      {
      echo $address;
      }
      else
      {
      echo "Not found";
      }
