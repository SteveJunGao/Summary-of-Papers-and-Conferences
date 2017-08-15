# DRAW: A Recurrent Neural Network For Image Generation
- From a high level view, DRAW combined VAE and RNN, generated image in a sequence. For the encoder and decoder part, it utilized attention machinism (for sequence).
- In detail, Encoder receives information from previous decoder part, at each time step, the model "read" some part and "write" some part (not a read the whole and predict part after part)
- for Attention, it defines a grid of Gaussian Filters. N*N grid, each one is a filter (filter the value from the neighbor). then we only need to predict the center position of the filter and the stride (stride means the displacement between each continuous grid)
