```mermaid
flowchart TB
    verify{Verify?}
    verify --> |Request| validate_field{"Validate field?"}
    validate_field --> |Yes| 21[Rule]
    validate_field --> |No|individual{Individual \n endpoints}
    individual --> |Yes| 11[Requests]
    individual --> |No| 22[Middleware]
    verify --> |Authorization| 68[Policy]

    verify --> |None| modify_request{Modify request?}
    modify_request --> |Yes| one_endoint{One endpoint?}
    one_endoint --> |Yes| 20[Request]
    one_endoint --> |No| 4323[Middleware]

    
    modify_request ----> |No| modify_response{Modify response?}
    modify_response --> |Yes| one_resource{"Apply to \n one resource?"}
    one_resource --> |Yes| resource[Resource]
    one_resource --> |No| 30[Middleware]

    modify_response --> |No| interact_with_something{Interact \n with something?}
    interact_with_something --> |Yes| triggered_by{"Triggered by?"}
    triggered_by --> |Event| 987[Listener]
    triggered_by --> |Database adjustment| 432[Observer]
    triggered_by --> |Http| 76[Controller]
    triggered_by --> |Other| hide_complexity{"Hide complexity?"}
    hide_complexity --> |Yes| behind_one_function{"Behind \n one fuction?"}
    triggered_by --> |Comment input| command_input{Command input?}
    command_input --> |Artisan migrate| 08[Migration]
    command_input --> |Other| 325[Command]

    behind_one_function --> |Yes| 321[Helper]
    behind_one_function --> |No| 323[Facade]
    hide_complexity --> |No| interact_with_database{"Interact with \n the database?"}
    interact_with_database --> |Yes| 90[Repository]

    interact_with_database --> |No| send_something{Send something?}
    send_something --> |Yes| 542[Notification]
     
    send_something --> |No| stand_alone_process{Stand-alone \n process?}
    stand_alone_process --> |Yes| 234[Job]
    stand_alone_process --> |No| need_return_value{Need \n return value?}
    need_return_value --> |Yes| 99[Service]
    need_return_value --> |No| 999[Action]
    
    interact_with_something --> |No| create_something{Create something?}
    create_something ---> |Yes| construct_dependency{Construct \n dependency \n injection?}
    construct_dependency --> |Yes| 876[Service Provider]
    construct_dependency --> |No| by_one_method{By one method?}
    by_one_method --> |Yes| 40[Factory Method]
    by_one_method --> |No| 41[Builder]
    create_something --> |No| hold_variable{Hold variable?}
    hold_variable --> |List| 49[Collection]
    hold_variable --> |Event| 598[Event]
    hold_variable --> |Value| dates_are_always_the_same{"Always the same?"}
    hold_variable --> |None| 382[Interface]
    dates_are_always_the_same --> |Yes| 8[Enum]
    dates_are_always_the_same --> |No| 9[Config]

    hold_variable --> |Other| transform{"Transform?"}
    transform --> |External data| 5[Adapter]
    transform --> |Database data| 6[Model]
    transform --> |Other| transform_data_in_multiple_steps{"Transform data \n in multiple steps?"}
    transform_data_in_multiple_steps --> |Yes| 14[Decorator]
    transform_data_in_multiple_steps --> |No| 15[Entity]
 ```
