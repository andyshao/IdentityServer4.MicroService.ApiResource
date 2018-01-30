# ˵��
���ڿ�������΢������Ŀ��ʾ�������ο��á�


#### ���ɲ���
* 1��Clone��ǰ��Ŀ����дҵ�����
* 2�����������з�����
* 3��ע�ᵽIdentityServer4΢������
```
��3����Ҫȷ���Ѿ��������
1,IdentityServer4.MicroService ����Ȩ���ģ�
2,IdentityServer4.MicroService.AdminUI ��΢����ͳһ����UI��
```


#### ����

##### 1 �Զ�����swagger����汾
![swagger](swagger.png)

##### 2 ������
```html
����Resources/Controllers�ṹ��Ӽ���,���Ʊ�����controller��Ӧ
```

##### 3 �Զ���΢�����Ȩ��/��ɫ
```csharp

        /*
        * ��չ��2���༴��
        */

        /// <summary>
        /// ClientȨ�޶���
        /// ��ӦToken�е�claim��scope�ֶ�
        /// �ֶ�������ȥcontroller �� action ���
        /// �ֶ�ֵ�����Ե�����
        /// �ֶ��Զ������ԣ����Ե�Ȩ�޼��ϣ�
        /// �ۺ�PolicyClaimValues���е�ֵ������"all"����ȥ�غ�Ǽǵ�IdentityServer��ApiResource��ȥ
        /// ����PolicyClaimValues("apiresource.create", "apiresource.all", "all"),����
        /// ��ǰapiresource��Ŀ��createȨ�ޣ����� apiresource.allȨ�ޣ�����allȨ��
        /// </summary>
        public class ClientScopes
        {
            [PolicyClaimValues(MicroServiceName + ".create", MicroServiceName + ".all", "all")]
            public const string Create = "scope:create";

            [PolicyClaimValues(MicroServiceName + ".read", MicroServiceName + ".all", "all")]
            public const string Read = "scope:read";

            [PolicyClaimValues(MicroServiceName + ".update", MicroServiceName + ".all", "all")]
            public const string Update = "scope:update";

            [PolicyClaimValues(MicroServiceName + ".delete", MicroServiceName + ".all", "all")]
            public const string Delete = "scope:delete";

            [PolicyClaimValues(MicroServiceName + ".approve", MicroServiceName + ".all", "all")]
            public const string Approve = "scope:approve";

            [PolicyClaimValues(MicroServiceName + ".reject", MicroServiceName + ".all", "all")]
            public const string Reject = "scope:reject";

            [PolicyClaimValues(MicroServiceName + ".upload", MicroServiceName + ".all", "all")]
            public const string Upload = "scope:upload";
        }

        /// <summary>
        /// UserȨ�޶���
        /// ��ӦToken�е�claim��permission�ֶ�
        /// �ֶ�������ȥcontroller �� action ���
        /// �ֶ�ֵ�����Ե�����
        /// �ֶ��Զ������ԣ����Ե�Ȩ�޼��ϣ��ɰ�������User���claims��permission����
        /// </summary>
        public class UserPermissions
        {
            [PolicyClaimValues(MicroServiceName + ".create", MicroServiceName + ".all", "all")]
            public const string Create = "permission:create";

            [PolicyClaimValues(MicroServiceName + ".read", MicroServiceName + ".all", "all")]
            public const string Read = "permission:read";

            [PolicyClaimValues(MicroServiceName + ".update", MicroServiceName + ".all", "all")]
            public const string Update = "permission:update";

            [PolicyClaimValues(MicroServiceName + ".delete", MicroServiceName + ".all", "all")]
            public const string Delete = "permission:delete";

            [PolicyClaimValues(MicroServiceName + ".approve", MicroServiceName + ".all", "all")]
            public const string Approve = "permission:approve";

            [PolicyClaimValues(MicroServiceName + ".reject", MicroServiceName + ".all", "all")]
            public const string Reject = "permission:reject";

            [PolicyClaimValues(MicroServiceName + ".upload", MicroServiceName + ".all", "all")]
            public const string Upload = "permission:upload";
        }
```

##### 4 ����
```html
<--��appsettings.json�ļ���-->
  "IdentityServer": ""��
  "ApiTrackerSetting": {
    "ElasticConnection": "",
    "DocumentName": "identityserver4-microservice-apiresource",
    "TimeOut": 500
  }

IdentityServer��identityserver4����Ȩ���ģ��ķ�������ַ���磺https://ids.ixingban.com
ApiTrackerSetting��elasticsearch�����ýڣ���ѡ
```