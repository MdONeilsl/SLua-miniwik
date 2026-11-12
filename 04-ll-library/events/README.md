# events

Callback signatures for every SLua event handler that a script can register through `LLEvents`.

| Path | Contents |
|---|---|
| [state_entry](state_entry.md) | Removed in SLua (no states) |
| [state_exit](state_exit.md) | Removed in SLua (no states) |
| [touch_start](touch_start.md) | Avatar begins touching |
| [touch](touch.md) | Ongoing touch |
| [touch_end](touch_end.md) | Touch released |
| [collision_start](collision_start.md) | Collision begins |
| [collision](collision.md) | Ongoing collision |
| [collision_end](collision_end.md) | Collision ends |
| [land_collision_start](land_collision_start.md) | Ground collision begins |
| [land_collision](land_collision.md) | Ongoing ground collision |
| [land_collision_end](land_collision_end.md) | Ground collision ends |
| [timer](timer.md) | Removed in SLua; use LLTimers |
| [listen](listen.md) | Chat on a listened channel |
| [on_rez](on_rez.md) | Object rezzed |
| [sensor](sensor.md) | Sensor finds matches |
| [no_sensor](no_sensor.md) | Sensor finds nothing |
| [control](control.md) | Avatar control input |
| [money](money.md) | L$ payment received |
| [email](email.md) | Email delivered |
| [at_target](at_target.md) | Reached llTarget position |
| [not_at_target](not_at_target.md) | Not yet at target |
| [at_rot_target](at_rot_target.md) | Reached rotation target |
| [not_at_rot_target](not_at_rot_target.md) | Not yet at rotation target |
| [run_time_permissions](run_time_permissions.md) | Permissions granted or revoked |
| [changed](changed.md) | Object properties changed |
| [attach](attach.md) | Attached or detached |
| [dataserver](dataserver.md) | Dataserver reply |
| [link_message](link_message.md) | Inter-script message |
| [moving_start](moving_start.md) | Movement begins |
| [moving_end](moving_end.md) | Movement ends |
| [object_rez](object_rez.md) | Rezzed another object |
| [remote_data](remote_data.md) | Removed in SLua (XML-RPC) |
| [http_response](http_response.md) | HTTP reply |
| [http_request](http_request.md) | Incoming HTTP request |
| [experience_permissions](experience_permissions.md) | Experience permission granted |
| [transaction_result](transaction_result.md) | L$ transfer result |
| [path_update](path_update.md) | Pathfinding status update |
| [experience_permissions_denied](experience_permissions_denied.md) | Experience permission denied |
| [linkset_data](linkset_data.md) | Linkset datastore change |
| [game_control](game_control.md) | Controller input update |
| [on_death](on_death.md) | Wearer health reached 0 |
| [on_damage](on_damage.md) | Damage inflicted |
| [final_damage](final_damage.md) | Damage applied |

