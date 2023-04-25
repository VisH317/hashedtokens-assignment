## GAN LSTM Data Passing

 * have two LSTMs with outputs of same input being concatenated
 * Input sequence => each through generator => provides output sequence
 * Each output from the generator => passed through discriminator => creates another output sequence
 * Generator output sequence passed in original order through LSTM 1
 * Discriminator output sequence passed in reversed order through LSTM 2 (reversed connections according to Bi-LSTM)
 * Discriminator + LSTM output reversed and corresponding elements concatenated with the corresponding generator outputs