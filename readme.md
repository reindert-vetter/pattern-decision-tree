Create a [pull request](https://github.com/reindert-vetter/pattern-decision-diagram/pulls) or start a [discussion](https://github.com/reindert-vetter/pattern-decision-diagram/discussions).

```mermaid
flowchart TB
    verify{Verify?}
    verify --> |Request| validate_field{"Validate field?"}
    validate_field --> |Yes| rule[Rule]
    validate_field --> |No|individual{Individual \n endpoint}
    individual --> |Yes| request1[Request]
    individual --> |No| middleware1[Middleware]
    verify --> |Authorization| policy[Policy]

    verify --> |None| modify_request{Modify request?}
    modify_request --> |Yes| one_endoint{One endpoint?}
    one_endoint --> |Yes| request2[Request]
    one_endoint --> |No| middleware2[Middleware]
    
    modify_request ----> |No| modify_response{Modify response?}
    modify_response --> |Yes| one_resource{"Apply to \n one resource?"}
    one_resource --> |Yes| resource[Resource]
    one_resource --> |No| middleware3[Middleware]

    modify_response --> |No| interact_with_something{Interact \n with something?}
    interact_with_something --> |Yes| triggered_by{"Triggered by?"}
    triggered_by --> |Event| listener[Listener]
    triggered_by --> |Database adjustment| observer[Observer]
    triggered_by --> |Http| controller[Controller]

    triggered_by --> |Other| hide_complexity{"Hide complexity?"}
    hide_complexity --> |Yes| behind_one_function{"Behind \n one fuction?"}
    triggered_by --> |Comment input| command_input{Command input?}
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
    
    interact_with_something --> |No| create_something{Create something?}
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
