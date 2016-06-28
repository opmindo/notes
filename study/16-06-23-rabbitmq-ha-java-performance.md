## Plan
* rabbitmq cluster and high availability
* read some ** Java Performance**

## Note
### cluster
> All data/state required for the operation of a RabbitMQ broker is replicated across all nodes. An exception to this are message queues, which by default reside on one node, though they are visible and reachable from all nodes.

```
rabbitmqctl join_cluster rabbit@rabbit2
rabbitmqctl set_policy ha-all "^ha\." '{"ha-mode":"all"}'
```
