---
title: Using a Custom Admin URL
---

As a [security best practice]({% link magento/magento-security-best-practices.md %}), Magento recommends that you use a unique, custom Admin URL instead of the default _admin_ or a common term such as _backend_. Although it will not directly protect your site from a determined bad actor, it can reduce exposure to scripts that try to gain unauthorized access.

{:.bs-callout-info}
Check with your hosting provider before implementing a custom Admin URL. Some hosting providers require a standard URL to meet firewall protection rules.

In a typical Magento installation, the Admin URL and path is immediately below the Magento base URL. The path to the store Admin is one directory below the root.

- **Default Base URL**: `http://yourdomain.com/magento/`
- **Default Admin URL and Path**: `http://yourdomain.com/magento/admin`

Although it is possible to change the Admin URL and path to another location, any mistake removes access to the Admin, and must be corrected from the server.

{:.bs-callout-info}
As a precaution, do not try to change the Admin URL by yourself unless you know how to edit configuration files on the server.

## Method 1: Change from the Magento Admin

1. On the _Admin_ sidebar, go to **Stores** > _Settings_ > **Configuration**.

1. In the left panel, expand _Advanced_ and choose **Admin**.

1. Expand ![Expansion selector]({% link images/images/btn-expand.png %}){: .Inline} the **Admin Base URL** section.

1. Set the configuration options for the custom URL:

    ![Advanced configuration - Admin base URL]({% link images/images/config-advanced-admin-admin-base-url.png %}){: .zoom}
    [_Admin Base URL_]({% link configuration/advanced/admin.md %})

    If needed, clear the **Use system value** checkbox to change the setting.

    - Set **Use Custom Admin URL** to `Yes`.

    - Enter the **Custom Admin URL**: `http://yourdomain.com/magento/`

        {:.bs-callout .bs-callout-info}
        The Admin URL must be in the same Magento installation, and have the same document root as the storefront.

    - Set **Custom Admin Path** to `Yes`.

    - Enter the **Custom Admin Path**.

        The path that you enter is appended to the Custom Admin URL after the last forward slash.

        `sample_custom_admin`

1. When complete, click <span class="btn">Save Config</span>.

1. After the changes are saved, **Sign Out** of the Admin. Then, log back in using the new Admin URL and path.

## Method 2: Change from the Server Command Line

1. Open the `app/etc/env.php` file in a text editor, and change the name of the `[admin]` path. Make sure to use only lowercase characters. Then, save the file.

    On the server, the _admin path_ is located in the `app/etc/env.php` file. Look for the `<adminhtml>` argument in the `<admin>` section:

    - **Default Admin Path**

        ```php?start_inline=1
        # <frontName><![CDATA[admin]]></frontName>
        ```
        {: .no-copy}

    - **New Admin Path**

        ```php?start_inline=1
        # <frontName><![CDATA[backend]]></frontName>
        ```
        {: .no-copy}

1. Use one of the following methods to clear the Magento cache:

    - On the _Admin_ sidebar, go to **System** > _Tools_ > **Cache Management**. Then, click **Flush Magento Cache**.
    - On the server, navigate to the `var/cache` folder and delete the contents of the `cache` folder.
