# C# Modules

Empire uses Covenant's yamls to import modules and run them through the Roslyn compiler. C# tasks are broken into two parts for Covenant and Empire. Everything external to section _Empire_ uses the formatting defined by Covenant's task, which additional documentation can be found [here](https://github.com/cobbr/Covenant/wiki/Building-Tasks).

### Empire Generation

C# modules have a section called _Empire_ in the yamls that defines Empire specific setting. These options are internal to Empire and will not be sent to the compiler. The Empire section of the yaml uses a similar formatting scheme as Python and PowerShell modules and an example of Empire yaml is below. This setup is used in the[ ProcessInjection module](https://github.com/BC-SECURITY/Empire/blob/master/empire/server/modules/csharp/ProcessInjection.Covenant.yaml#L92).

```
    software: ''
    techniques:
      - ''
    background: true
    output_extension:
    needs_admin: false
    opsec_safe: false
    comments:
      - ''
    options:
        - name: ''
        description: ''
        required: true
        value: ''
```

### Advanced Generation

**custom\_generate:** For complex modules that require custom code that accesses Empire logic, such as lateral movement modules dynamically generating a listener launcher, a custom "generate" function can be used. To tell Empire to utilize the custom generate function, set `advanced.custom_generate: true`

Additional information about custom\__generate can be found under the_ [_PowerShell Modules custom\_generate_](https://bc-security.gitbook.io/empire-wiki/module-development/PowerShell-Modules#advanced)_._
