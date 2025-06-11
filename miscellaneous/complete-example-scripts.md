# Complete Example Scripts

Here are some complete example scripts, [taken from the CK Wiki](https://ck.uesp.net/wiki/Complete_Example_Scripts) and translated into PaperScript. All credit goes to the original authors.

### A Simple Toggle

```rust
script SimpleToggle : ObjectReference {
  toggle: Bool = false
  
  event OnActivate(actionRef: ObjectReference) {
    toggle != toggle
    
    if toggle {
      // Do Stuff
    } else {
      // Do Stuff
    }
  }
}
```

Attach this script to an activator like a button, lever or container.

### A Quest object that sets stages and objectives when it's picked up and dropped repeatedly

```rust
script DroppableQuestObject : ObjectReference {
    auto property PlayerREF: Actor
    
    // Fill this with the quest this item is for
    auto property FromQuest: Quest

    // Should the quest get "uncompleted" when the item is dropped?
    auto property UncompleteEnabled: Bool = true

    // At which quest stage should the script stop working?
    auto property StageToStopQuestItem: Int = 99999

    // What stage should the quest be set to when the item is picked up?
    auto property StageToSetOnPickup: Int = -1

    // Which objective should be displayed when the item is picked up?
    auto property ObjectiveToDisplayOnPickup: Int

    // Which objective should be completed when the item is picked up?
    auto property ObjectiveToCompleteOnPickup: Int

    // Which stage should the quest be set to when the item is dropped?
    auto property StageToSetOnDrop: Int = -1

    // Which objective should be displyed when the item is dropped?
    auto property ObjectiveToDisplayOnDrop: Int

    // Which objective should be hidden when the item is dropped?
    auto property ObjectiveToHideOnDrop: Int = -1

    event OnContainerChanged(newContainer: ObjectReference, oldContainer: ObjectReference) {
        if FromQuest.GetStage() < StageToStopQuestItem {
            if oldContainer == PlayerREF {
                FromQuest.SetObjectiveDisplayed(ObjectiveToDisplayOnDrop, true, true)
			    FromQuest.SetObjectiveDisplayed(ObjectiveToHideOnDrop, false)

                if UncompleteEnable {
                    FromQuest.SetObjectiveCompleted(ObjectiveToCompleteOnPickup, false)
                }

                if StageToSetOnDrop >= 0 {
                    FromQuest.SetStage(StageToSetOnDrop)
                }
            } elseif NewContainer == PlayerREF {
                FromQuest.SetObjectiveDisplayed(ObjectiveToDisplayOnPickup, true, true)
			    FromQuest.SetObjectiveCompleted(ObjectiveToCompleteOnPickup)

                if StageToSetOnPickup >= 0 {
                    FromQuest.SetStage(StageToSetOnPickup)
                }
            }
        }
    }
}
```

Attach the script to the relevant item and fill all the properties accordingly.

### A Trigger that activates when the Player enters it

```rust
script ExampleTrigger : ObjectReference {
    auto property PlayerREF: Actor

    event OnTriggerEnter(actionRef: ObjectReference) {
        if actionRef == PlayerREF {
            Debug.MessageBox("Player Entered")
        }
    }
}
```
