# evote-movie-2019-07-movie-list-from-array

Part of the progressive Movie Voting website project at:
https://github.com/dr-matt-smith/evote-movie-2019

The project has been refactored as follows:


- in `/src/controllerFunctions.php` 

    - in the `listAction()` function declare an array `movies` that contains an array for each movie to be displayed, using keys `id`, `title` and `price`:

        ```php
            function listAction()
            {
                $movies = [];
                $movies[] = [
                    'id' => 1,
                    'title' => 'Jaws',
                    'price' => 10.00
                ];
                $movies[] = [
                    'id' => 2,
                    'title' => 'Aliene',
                    'price' => 19.99
                ];
                $movies[] = [
                    'id' => 3,
                    'title' => 'Shrek',
                    'price' => 10.00
                ];
            
                $pageTitle = 'list';
                $listPageStyle = 'current_page';
                require_once __DIR__ . '/../templates/list.php';
            }        
        ```
        

- in `/templaters/list.php` 

    - add in a FOREACH-loop to loop through array `$movies` diplaying the id, title and price as table row for each element:
    
        ```php
          <table>
              <tr>
                  <th> ID </th>
                  <th> title </th>
                  <th> price </th>
              </tr>
          
              <?php
                  foreach($movies as $movie):
              ?>
          
                  <tr>
                      <td><?= $movie['id'] ?></td>
                      <td><?= $movie['title'] ?></td>
                      <td>&euro; <?= $movie['price'] ?></td>
                  </tr>
          
              <?php
                  endforeach;
              ?>
          
          </table>
        ```
        
    - NOTE: the use of the ` foreach($movies as $movie):` and `endforeach;` statements - to avoid large sections of code in an `{...}` block
    
        - see [http://php.net/manual/en/control-structures.alternative-syntax.php](http://php.net/manual/en/control-structures.alternative-syntax.php)
        
        
