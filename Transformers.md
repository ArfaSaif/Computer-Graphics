
- ![image](https://user-images.githubusercontent.com/48233453/162028776-4387d011-5df9-4134-83bf-e4b42add8aa3.png)

- models that operate on the sequences
- specifically actually they operate on sets
- so you'd have a set of words which you can characterize as tokens 
-  then the transformer take all of these in and do  attention quadratic operation which basically means that you have to calculate the pairwise inner product between each of these between each pair of the of these bubbles which becomes a very very large task very quickly
- many many interconnections 
- 500 tokens long you need 500 squared connections so
- but if you want to feed this into a transformer you have to think that every single location here every single pixel has to attend to every single other pixel
- so the attention will cost you 250 squared squared

- so people have resorted to other things doing things like only local attention so only attending to the kind of area around them which of course is the the foundational motivation behind convolutional neural networks is that you learn kernels that are local and then 
you you kind of slide them across and over the layers, layer to layer so
-  ![image](https://user-images.githubusercontent.com/48233453/162057917-7d675831-10ec-439a-9067-688abff0a529.png)
-  -the first layer this part might attend to like a cone around itself and this part might in the same cone will have a larger receptive field right so in this the receptor field grows by depth however transformers are able to attend within a single layer to everywhere

This paper
- let's do global attention by simply going over image patches
- so they divide the image into these patches as you can see here and one patch is in this case something like 16 by 16.
- they unroll these patches into a sequence which is a in first instance it's a set they combine this with a positional embedding so
- 
the transformers naturally they have no idea what what is 

- the transformer in a way is a generalization of an mlp of a feed-forward network in a feed-forward network what you have is you have
- -  mlp knows where information comes from the transformer doesn't the transformer computes on the fly and therefore is permutation and variant
![image](https://user-images.githubusercontent.com/48233453/162059409-1e397d05-fdf7-490e-9846-d09d2fb90bf3.png)

- permutation and variant 
and that's why a lot of applications add to the inputs these so-called positional embeddings. these are learnable embeddings so you don't actually feed the number but what you have is you have a table and the table will say we'll have these indices and each one is associated with a vector and these vectors are learnable parameters so whenever you say 
this is the first patch what you actually do is you go here you grab the vector to the number one
- so you have to get that somehow into a form where the transformer can understand it
- one single matrix and this one single 
matrix is called
- they take a patch like this they unroll it so here you have the you multiply that vector with the embedding matrix and that's what goes into the transformer along with the position embedding in this case we have position embedding
- ![image](https://user-images.githubusercontent.com/48233453/162060140-29cae000-6057-4154-a231-1a904a70b90d.png)
- the multi-head attention that's the expensive operation so the paper completely
- ![image](https://user-images.githubusercontent.com/48233453/162060509-30c33622-7f1c-4475-8da7-265541333ff5.png)
- 
 so the paper completely completely discards the notion of convolutions
 
 ![image](https://user-images.githubusercontent.com/48233453/162061829-a192a5c4-baa7-4ec2-8092-def770630069.png)
  even though you never tell it you simply let it learn where this patch is in the image
![image](https://user-images.githubusercontent.com/48233453/162061940-825d7a2e-4fa5-43fb-8303-37825ce427d4.png)
the mean attention distance so the the  distance increases and from like the middle of the network you pretty much have global computation 
![image](https://user-images.githubusercontent.com/48233453/162062404-99fdbaef-7eb0-4c1f-9f7b-6343aca3c7cc.png)


the additional benefit you get in the transformers is of course that at the very beginning you can already pay attention to things that are very far away you cannot do that with convolutional networks or when you use local attention

lstms introduced transforms - now replaces lstms, and now replacing convoutions

21:57
an mlp a feed forward network like we looked at here the the the notion should be that it could technically learn any function right a feedforward network can technically learn any function but it's it's kind of unstable and so on you know if you shift by a pixel all the inputs are all weird and so on so a 
convolutional neural network for images seemed pretty good because it has a good inductive prior and the good inductive prior is this is that probably what a one pixel cares about is its immediate neighborhood and then what that neighborhood as a whole cares about is its immediate neighborhood right so that's sort of how we look at images like you integrate over small regions and then you connect the regions to each other and so on so
- we introduced a bias into a model by saying that we will be using a convolutional network, or lstm, these help the model be good at tasks. This is when we dont have anough data. it will bias our estimator, it will bot be the expected value matches the actual underlying thing
- but now we have more data, now a biased model will not do as good. Transformers are not another architecture, are omre general than mlp - people think mlp connected to everything , so people thik its the omst general
- but here the connections are calculate don the fly
- less specialized mlp - its just the fact that its a general computer - can feed it enough data that it can learn the things - can learn the useful biases - it learns similar filters to convolutions - 
