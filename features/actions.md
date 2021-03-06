# Claims

Claims are the main way to create new tokens for your community. We use the concept of Objectives and Actions.

### Objectives

Objectives are what you want to achieve with your actions. All actions must be done towards a bigger objective. We recommend giving a through description to your objectives and try to add an expected result for it: a **good** result and a **great** result. This will help you get a better grasp on how your expectations are aligned with the reality.

### Actions

Actions are the definition of exactly what the community must do to reach those objectives. We made actions in a way that they are very flexible and allow for different use cases. For that we added a few options:

**_Validity_ of an action. This can be by _date_ and _quantity_**
  - _Date_: An action can be claimed until certain date is reached. After the set date, claims cannot be opened. The validation of opened claims can occur after the set date.
  - _Quantity_ : Determines the number of times this action can be **Approved or Disapproved**. That means that the users can claim all they want, but only the specified number can lead to rewards. So lets say we configure this action to have `Quantity of 3`; we can have 100s of claims opened, but after the 3 one is voted fully (approved or disapproved) the rest will be "unvoteable:, as the action will change its status to "completed" (that is set the flag `is_completed` to `true`). Quantity is about **claims**. 
 
Example of a sceario using **Quantity**
> Lets say you create an action called "Plant a tree", that belongs to an objective called "Plant 2 trees". In this case, we configure that action to have `quantity` as 2. That is, after the community has verified that exactly 2 trees were planted, the action will be considered completed. Lets say that this community had high engagement, and a lot of users have claimed to plant trees. Lets assume that we had 10 claims open. Now the verifiers of that **action** will have check and give their vote on each **claim**. Lets say that they disapprove the first, approved the second. When its time to vote for the third one, their vote will fail. The action be considered completed. After that, all other claims will not be votable.
  
**Verification**

Verification is the process by which the community decides if an action is completed or not. The verification process can be Automatic if validated by software, or Manual, which requires human validation.


  - _Automatic_: This validation requires nothing more than a contract call, it will reward the users directly as specified in the [`verifyaction`](https://github.com/cambiatus/contracts/blob/master/community/community.hpp#L202) function. This function requires an `maker` param which will be the user rewarded. Those actions were created aiming for automation from the communities to give rewards based of a process that is automatically verified. For example, on the [Entre Pulperias](https://www.facebook.com/entrepulperoscostarica/) app, the users earn tokens by doing e-learning classes. Since the software can tell if they actually did the class, the rewarding can be made without human interaction
  - _Manual_: As the name implies, it requires manual verification before rewarding. Basically it means that we need human verification and interaction in order to reward the users for doing an action for their community. It allows us to configure a number of verifications and require us to have an odd numbers of validators. I think its not the best context to explain in more depth about those rules, but we do have to find a way to settle the voting, and we use [Supermajority](https://en.wikipedia.org/wiki/Supermajority#Majority_of_the_entire_membership) voting system.
  
#### Manual verification of Actions

Manually requiring humans to verify that an action was done means that we need to open a process to validate votes. This process is called **Claim**. 

`Create action -> Claim action -> Voting -> Rewarding`

It all starts when a user opens a new claim
