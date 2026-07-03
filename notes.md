I have been building ML and DL models , while exploring the field of medical imaging and using AI in medical , I found this paper quite interesting and it resonated with me well because I faced a similar dilemma of comprising interpretabilty for accuracy with nueral nets. 

The exact architecture and science behind the concept can only be truly understood with reading the paper but in my words I would say that its a mechanisim of having two weightages that tell how important or unimportant a single visit to the doctor and a single medical diagnosis was in terms of one being diagnosed with a particular disease , in our case Heart Failure. 

Flow is: 

Patient visit sequence
↓
[Embedding layer — 582 ICD codes → 128-dim vectors]
↓
visit representations (one 128-dim vector per visit)
↙                       ↘
[GRU_α — reversed]      [GRU_β — reversed]
↓                       ↓
[Linear → scalar]       [Linear → vector]
↓                       ↓
[Softmax]               [Tanh]
↓                       ↓
alpha α               beta β
(visit importance)  (code importance)

Both of these combine to form the: 

α * β * visit_repr → sum
↓
context vector
↓
[Output layer]
↓
ŷ = risk score
