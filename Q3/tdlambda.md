## TD(λ)

_Overview:_ TD(λ) is a variation of reinforcement learning method that combines Monte Carlo methods and temporal difference methods

**Background:**
 * Monte Carlo methods - goes through an episode, averages the rewards for each state-value or action-value pair, and uses that to update the policy
 * Temporal Difference Learning - Uses bootstrapping, allows predictions of value functions to be made based on previous predictions
   * Unlike Monte Carlo: allows online updates, using previous value functions allows TD to generalize faster
 * Differences: Monte Carlo involves averaging the return over the whole training period, while TD learning involves taking only the prediction of the next state as input
 * TD(λ) is a combination => uses the λ parameter to control how far into the future to look - balance between monte carlo and TD

**TD(λ) theoretical view:**
 * sum of n-step TD method for all future timesteps, with the lambda as a gradually decreasing weight to weigh states that are farther from the current state less in the current update
 * λ parameter - controls the combination between TD and Monte Carlo
   * When λ=1: all future returns will be considered, basically the same as Monte Carlo
   * When λ=0: only the next reurn will be considered, same as TD(0)
 * Overall equation for updating value function: sum of all future value function calculations, where each one in the future is multiplied by an extra λ value
   * Takes future steps into account, but weights closer ones more 
   * The weight will diminish the importance of states far in the future over time
 * Called λ-return - an offline method that can be used to calculate value functions based on future value states after an episode is completed

**On Policy version using Eligibility Traces:**
 * Unlike λ-return, the on policy version looks to previous states instead of future states
 * While the forward-looking λ-return method weights an action based on the predicted future returns, the backward method updates previous action values based on their contribution to the reward of the current step
 * Eligibility trace - function applied to each state to keep track of their frequency at different points in the episode (reset at beginning of each episode)
   * Usually involves adding to the specific state's trace value when the state is reached, and diminishing over time when state is not seen for some time
   * Accumulating trace: adds 1 to the trace for a state when the state is reached
   * Replacing trace: sets the trace value to 1 for  a state when it is reached
   * Dutch trace - weights the previous eligibility trace with an alpha parameter - causes high-frequency states to slow down in their eligibility trace increase over time
 * Eligibility trace decreases over time - * λ is applied over time to replicate a slow decreases when the state is not visited as frequently
 * Method:
   * Choose an action and receive new state and reward
   * Calculate the TD error: similar to advantage function by predicting as reward + value_function(new_state) - value(previous_state)
   * Eligibility trace updated for the new state
   * for each state in value function: add step_size * TD * eligibility trace
   * Update eligibility trace to decrease by one lambda factor (λ) to show decrease over time with less frequency


_Conclusion: Why is TD(λ) better than previous methods?_
 * TD(λ) is able to evaluate the frequency of previous actions => assumes states that were more frequent contributed more to the overall reward of the state
 * Able to reason the cause for the reward received based on previous actions and alter that action accordingly