# entity-activity-as-gnome
a repo to hold tendency of an entity in a finite possible environment

: language [python 3.6 and clojure]
: input [json or array of json]
: db used [mysql and redis]
Usecase :

to translate entity behavior in an environment using following steps : reads -> contig -> scaffolding -> a long sequence of string [a chromosome]

then based on upcoming activites to updatae final string and generate tendencies based on arrival of events 

arriving events will be processed in real time and will be transmitted to timeline queues maintained in redis [toplogies will be written in clojure]

one activity is poped from a timeline q sequence string will start getting generated , expected behavior is that with time cerain entities will pop more events form certain timeline q and less or zero from certain (call this behavior tendency).

tendency will be calculated based on reinforcement learning.

[final : a fixed database for an environemnt for a certain set of entity and then to observe which entity have the superior genome (onece this generated timeline q's can be manipulated to either observe or to change future bahavior)]


intial environment is a game to get maximum sum from consumed events:
intially there are 5 timeline q's:
q{i} = a json {"act1":[a,b,c...]} a,b,c can be +/- intigers
constrains of the game :
1. while an entity is consuming from a timeline q [tq] only 1/3rd more can do so from samae tq either a player can wait or consume from another tq
2. a player (entiry) has to take the sum of numers in a tq and hold it till next consumption
3. if time line are arranged in [1,2,3,4,5] a player wo consumed from ith tq can not consume form tq at index< i-x [order of q is cyclic] [x not decided , it's a factor that will add to tendency as one would like to achieve maximization by replicating a behavior which rewaded him before]
4. entity can chose to consume or to wait.
5. if a players present reaches a negative threashold , his window for current consumption tq will decline i.e x becomes less.

the game is infinite and will go on , task is to build a learning layer where entities decide based on their past evaluation [a string] to wait of to cosume from a tq in present granted window.


[activities can be replaced by any activity]


[to be changed]


 
