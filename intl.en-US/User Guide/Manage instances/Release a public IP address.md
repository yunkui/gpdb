# Release a public IP address {#concept_dvb_xjx_yfb .concept}

If the network environment changed after the Internet address is allocated, you can release the Internet address on HybridDB for PostgreSQL console if you don't need it any more. After releasing the Internet address, make sure to change the application configurations which related to this address. Before performing this operation, please read the following scenarios.

Before performing this operation, please read the following scenarios.

## Scenarios { .section}

Public IP addresses and internal IP addresses are used in the following scenarios:

-   Use internal IP addresses only:
    -   Your application is deployed on an ECS instance in the same region as your HybridDB for PostgreSQL instance and shares the same [network type](../../../../reseller.en-US/Quick Start/Set up an instance/Set the network type.md#) with the ECS instance.
-   Use the public IP addresses only:
    -   The ECS instance where your application is deployed and your HybridDB for PostgreSQL instance are in different regions.
    -   Your application is deployed in a third-party system other than Alibaba Cloud.
-   Use both public and internal IP addresses:
    -   Some application modules are deployed on an ECS instance in the same region with the same [network type](../../../../reseller.en-US/Quick Start/Set up an instance/Set the network type.md#), while other modules are deployed on an ECS instance in a different region.
    -   Some modules of the application are deployed on an ECS instance in the same region with the same [network type](../../../../reseller.en-US/Quick Start/Set up an instance/Set the network type.md#), while other modules are deployed in systems other than Alibaba Cloud.

## Procedure { .section}

1.  Log on to the [HybridDB for PostgreSQL console](https://partners-intl.console.aliyun.com/#/gpdb).
2.  Select the **Region** of the instance.
3.  Locate the target instance. In the Actions column, click **Manage**.
4.  Click **Database Connection** on the left-side navigation.
5.  On the Database Connection page, Click **Release Internet Address**.

    If you haven't applied for an Internet address since you created an instance, there is only **Apply for internet address** on the Database Connection page.

6.  Click **OK** on the dialog box to release the Internet address.

