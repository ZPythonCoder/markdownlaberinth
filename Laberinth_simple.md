```ruby
#by Zee Marquez Wehmeyer 05/01/2019
#This program checks if a given path solves for a laberinth



def checkpath(laberinth,path,startpos,endpos):
    doespathsolve = False
    i_0 = startpos[0]
    j_0 = startpos[1]
    i_max = endpos[0]
    j_max = endpos[1]
    i, j = i_0, j_0
    for step in path:

        previouspos = [i,j] #stores the previous position
        if (step == "d" and i<i_max):
            i = i + 1
        if (step == "u" and i>i_0):
            i = i - 1
        if (step == "r" and  j<j_max):
            j = j + 1
        if (step == "l" and j>j_0):
            j = j - 1

        currentpos = [i,j]
        print('Step:',step,' Previouspos:',previouspos,' Position:',currentpos)

        if [i,j] == [i_max,j_max]:
            print("\nPath finished the laberinth \n")
            doespathsolve = True
            break
        if [i,j] == previouspos:
            print("The path is trying to pass the limits of the laberinth \n")
            doespathsolve = False
            break
        if laberinth[i][j] == 0: #encountered a wall, program must stop and return doespathsolve = False
            doespathsolve = False
            break
        elif laberinth[i][j] == 1:
            doespathsolve = True
    return doespathsolve


laberinth = [
                        [1,0,0,0,0],
                        [1,1,0,1,0],
                        [1,0,1,1,1],
                        [1,1,1,0,1],
                        [1,0,0,0,1]
                    ]

print('Laberinth Size:',len(laberinth),'x', len(laberinth[0]) ,'\n')
print(laberinth,'\n')
startpos =  [0,0]
endpos =    [4,4]
path = ["d","d","d","r","r","u","r","r","d","d"]
print('Path:',path, '\n')

laberinthsolve = checkpath(laberinth,path,startpos,endpos)
if laberinthsolve:
    print('\nThe path does solve for the given laberinth correctly')
else:
    print('\nThe path is incorrect')

```
