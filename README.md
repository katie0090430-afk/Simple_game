
# Simple_game






#include <iostream>
using namespace std;

struct object
{
    int x;  
    int y;
    char icon;
};

 void draw(char map[10][20])
 
{
    for(int i = 0; i < 10 ;i++)
    
    {
      
      for(int j = 0; j < 20; j++)
      {
         cout<<map[i][j];
      } 
         cout<<endl;
         
            }
       }
          
 void clearmap(char map[10][20])
 {
     for (int i = 0 ; i < 10 ; i++)
        for (int j = 0; j < 20 ;j++)
            map[i][j] = ' ';
 }
 
  void placeobjects (char map[10][20], object player, object enemy, int enemyalive )

  { 
      map[player.y][player.x] = player.icon;
         if(enemyalive == 1)
            map[enemy.y][enemy.x] = enemy.icon;
  }
  
   void moveshot(object  &shot, int  &vy, int gravity)
   {
   
   shot.x += 1;
   shot.y += vy;
   vy += gravity;
   
     }
     
    void hit(object shot, object enemy, int &enemyalive, int &shotalive, int *scoreptr)
     {
         if(shot.x == enemy.x && shot.y == enemy.y)
         {
             enemyalive = 0;
             shotalive = 0;
             *scoreptr += 100;
         }
     }
     
   void game( )  
   {
      char map[10][20];
      
      object player = {1, 8, 'P'};
      object enemy = {15, 8, 'E'};
      object shot = {1, 8, '*'};  
      
      
     int enemyalive = 1;
     int shotalive = 0;
     
     
     int vy = 0;
     int gravity = -1;
     
     
     int score = 0;
     int *scoreptr = &score;
     
     while (true) 
     { 
         clearmap(map);
         placeobjects(map, player, enemy, enemyalive);
         
         if (shotalive == 1)
         {
             moveshot(shot, vy, gravity);
             hit(shot, enemy, enemyalive, shotalive, scoreptr);
             
             
            if (shot.x >= 19 || shot.y < 0 || shot.y >=9)
               shotalive = 0;
             
             else 
                  map[shot.y][shot.x] = shot.icon;
         }
         
         draw(map);
         
         cout<< "score:?" << score << endl;
         cout<<"Enter=Tick |s=Shoot | q= QUIT\n";
         
         char c;
         cin.get(c);
         
         if(c == 'q')
            break;
            
             if(c == 's' && shotalive == 0)
         
               { 
               shot.x = player.x;
               shot.y = player.y;
               shotalive = 1;
               vy = 0;
     }
    
          } 
          
               }
               
               
               
               
               
               int main( )
               {
                   int choice;
                   
                   while (true)
                   {
                       cout<<"1.start game\n";
                       cout<<"2.help\n";
                       cout<<"3.exit\n";
                       
                       cin>>choice;
                       cin.ignore( );
                       
                       
                       switch(choice)
                       {
                           case 1:
                              game( );
                              break;
                             
                             
                            case 2:
                                cout<<"P =Player\n";
                                cout<<"* = shot\n";
                                cout<<"E = enemy\n";
                                cout<<"press enter\n";
                                cin.get( );
                                  break;
                                
                                case 3:
                                   return 0;
                       }
                   }     
               }
                        
                               
                      
                  
               
               
            
    
            
         
         
      
      
    
         






