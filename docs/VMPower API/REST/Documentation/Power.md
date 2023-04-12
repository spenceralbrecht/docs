# Power

The Power API allows you to power on or off a virtual machine. The API returns a long-polled response and returns when the VM power on/off action is completed.

## Operations

### POST /power

#### URL Query Parameters

- `instance-id` - (ID) The Virtual Machine `instance-id` field

- `action` - (String) Either `off` or `on`

Responds with `Success` or `Errors` object

```json
{
    status: "succeeded"
}
```
