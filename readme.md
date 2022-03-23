# Pattern Decision Tree

Ever wondered which file your code should be in? Based on this tree you can determine what kind of code you are working with.

The diagram was created with [Mermaid](https://mermaid-js.github.io/mermaid/#/). So you can easily make adjustments [yourself](https://github.com/reindert-vetter/pattern-decision-tree/edit/main/readme.md) or start a [discussion](https://github.com/reindert-vetter/pattern-decision-diagram/discussions).

```mermaid
flowchart TB
    verify{Verify?}
    verify --> |Request| validate_field{"Validate field?"}
    validate_field --> |Yes| multiple{Multiple?}
    multiple --> |Yes| form_request1[Form Request]
    multiple --> |No| rule[Rule]
    validate_field --> |No| middleware1[Middleware]
    verify --> |Authorization| policy[Policy]

    verify --> |No| modify_request{Modify request?}
    modify_request --> |Yes| one_endpoint{One request?}
    one_endpoint --> |Yes| form_request2[Form Request]
    one_endpoint --> |No| middleware2[Middleware]
    
    modify_request ----> |No| modify_response{Modify response?}
    modify_response --> |Yes| because_of_an_error{"Because of \n an error?"}
    because_of_an_error --> |Yes| exception[Exception]
    because_of_an_error --> |No| one_resource{"Apply to \n one resource?"}
    one_resource --> |Yes| resource[Resource]
    one_resource --> |No| middleware3[Middleware]

    modify_response ---> |No| logic{"It it business logic?"}
    logic --> |Yes| triggered_by{"Triggered by?"}
    triggered_by --> |Event| listener[Listener]
    triggered_by --> |Database adjustment| observer[Observer]
    triggered_by --> |Http| controller[Controller]

    triggered_by ---> |Other| hide_complexity{"Hide complexity?"}
    hide_complexity --> |Yes| behind_one_function{"Behind \n one function?"}
    triggered_by --> |Command input| command_input{Command input?}
    command_input --> |Artisan migrate| migration[Migration]
    command_input --> |Other| command[Command]

    behind_one_function --> |Yes| helper[Helper]
    behind_one_function --> |No| facade[Facade]
    hide_complexity --> |No| interact_with_database{"Interact with \n the database?"}
    interact_with_database --> |Yes| repository[Repository]

    interact_with_database --> |No| send_something{Send something?}
    send_something --> |Yes| notification[Notification]
     
    send_something --> |No| stand_alone_process{Stand-alone \n process?}
    stand_alone_process --> |Yes| job[Job]
    stand_alone_process --> |No| need_return_value{Need \n return value?}
    need_return_value --> |Yes| service[Service]
    need_return_value --> |No| action[Action]
    
    logic --> |No| create_something{Create something?}
    create_something ---> |Yes| construct_dependency{Construct \n dependency \n injection?}
    construct_dependency --> |Yes| service_provider[Service Provider]
    construct_dependency --> |No| by_one_method{By one method?}
    by_one_method --> |Yes| factory_method[Factory Method]
    by_one_method --> |No| builder[Builder]
    create_something --> |No| hold_variable{Hold variable?}
    hold_variable --> |List| collection[Collection]
    hold_variable --> |Event| event[Event]
    hold_variable --> |Value| dates_are_always_the_same{"Always the same?"}
    hold_variable --> |None| interface[Interface]
    dates_are_always_the_same --> |Yes| enum[Enum]
    dates_are_always_the_same --> |No| config[Config]

    hold_variable --> |Other| transform{"Transform?"}
    transform --> |External data| adapter[Adapter]
    transform --> |Database data| model[Model]
    transform --> |Other| transform_data_in_multiple_steps{"Transform data \n in multiple steps?"}
    transform_data_in_multiple_steps --> |Yes| decorator[Decorator]
    transform_data_in_multiple_steps --> |No| entity[Entity]
 ```
