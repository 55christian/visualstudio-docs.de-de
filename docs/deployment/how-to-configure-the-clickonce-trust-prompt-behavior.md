---
title: 'Vorgehensweise: Konfigurieren des Verhaltens der ClickOnce-Vertrauensstellung Prompt | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- deploying applications [ClickOnce], trust prompt
- ClickOnce applications, install without prompting
- ClickOnce applications, trust prompt
- ClickOnce deployment, trust prompt
ms.assetid: cc04fa75-012b-47c9-9347-f4216be23cf2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9ec30f3200b5a1df587713a2ee2394f52e3fb333
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62899825"
---
# <a name="how-to-configure-the-clickonce-trust-prompt-behavior"></a>Vorgehensweise: Konfigurieren des Verhaltens der ClickOnce-Eingabeaufforderung zur Vertrauenswürdigkeit
Sie können die ClickOnce-vertrauensaufforderung, um zu steuern konfigurieren, ob Benutzer die Option zum Installieren der ClickOnce-Anwendungen, z. B. Windows Forms-Anwendungen, Windows Presentation Foundation-Anwendungen, konsolenanwendungen, WPF-Browser angegeben werden Anwendungen und Office-Projektmappen. Sie konfigurieren die vertrauenswürdige Eingabeaufforderung durch Festlegen von Registrierungsschlüsseln für jeden Computer des Benutzers.

 Die folgende Tabelle zeigt die Konfigurationsoptionen, die auf jede der fünf Zonen (Internet, UntrustedSites, Arbeitsplatz, LocalIntranet und TrustedSites) angewendet werden können.

|Option|Festlegen des Registrierungswerts|Beschreibung|
|------------|----------------------------|-----------------|
|Ermöglichen Sie die vertrauenswürdige Eingabeaufforderung.|`Enabled`|Der ClickOnce-vertrauensaufforderung ist angezeigt, sodass Endbenutzer Vertrauensstellung für ClickOnce-Anwendungen erteilen können.|
|Beschränken Sie die vertrauenswürdige Eingabeaufforderung.|`AuthenticodeRequired`|Der ClickOnce-vertrauensaufforderung wird nur angezeigt, wenn die ClickOnce-Anwendungen mit einem Zertifikat signiert sind, die den Herausgeber identifiziert.|
|Deaktivieren Sie die vertrauenswürdige Eingabeaufforderung.|`Disabled`|Der ClickOnce-vertrauensaufforderung wird nicht für jede ClickOnce-Anwendungen angezeigt, die nicht mit einem explizit vertrauenswürdigen Zertifikat signiert sind.|

 Die folgende Tabelle zeigt das Standardverhalten für jede Zone. Die Spalte Anwendungen bezieht sich auf Windows Forms-Anwendungen, Windows Presentation Foundation-Anwendungen, konsolenanwendungen und WPF-Webbrowseranwendungen.

|Zone|Anwendungen|Office-Projektmappen|
|----------|------------------|----------------------|
|`MyComputer`|`Enabled`|`Enabled`|
|`LocalIntranet`|`Enabled`|`Enabled`|
|`TrustedSites`|`Enabled`|`Enabled`|
|`Internet`|`Enabled`|`AuthenticodeRequired`|
|`UntrustedSites`|`Disabled`|`Disabled`|

 Sie können diese Einstellungen überschreiben, indem aktivieren, beschränken oder der ClickOnce-vertrauensaufforderung deaktivieren.

## <a name="enable-the-clickonce-trust-prompt"></a>Aktivieren der ClickOnce-vertrauensaufforderung
 Aktivieren Sie die vertrauenswürdige Eingabeaufforderung für eine Zone aus, wenn der Endbenutzer mit der Option installieren und Ausführen einer beliebigen ClickOnce-Anwendung, die von dieser Zone ist angezeigt werden sollen.

#### <a name="to-enable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Um die ClickOnce-vertrauensaufforderung zu aktivieren, indem Sie den Registrierungs-editor

1. Öffnen Sie den Registrierungs-Editor ein:

    1. Klicken Sie auf **Start** und dann auf **Ausführen**.

    2. In der **öffnen** geben `regedit`, und klicken Sie dann auf **OK**.

2. Suchen Sie den folgenden Registrierungsschlüssel:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     Wenn der Schlüssel nicht vorhanden ist, erstellen Sie ihn aus.

3. Fügen Sie die folgenden Unterschlüssel als **Zeichenfolgenwert**, wenn sie nicht bereits mit den zugeordneten, in der folgenden Tabelle angezeigten Werten vorhanden sind.

    |Unterschlüssel für Zeichenfolge-Wert|Wert|
    |-------------------------|-----------|
    |`Internet`|`Enabled`|
    |`UntrustedSites`|`Disabled`|
    |`MyComputer`|`Enabled`|
    |`LocalIntranet`|`Enabled`|
    |`TrustedSites`|`Enabled`|

     Bei Office-Projektmappen `Internet` hat den Standardwert `AuthenticodeRequired` und `UntrustedSites` hat den Wert `Disabled`. Für alle anderen `Internet` hat den Standardwert `Enabled`.

#### <a name="to-enable-the-clickonce-trust-prompt-programmatically"></a>Um die ClickOnce-vertrauensaufforderung programmgesteuert zu aktivieren.

1. Erstellen Sie eine Visual Basic oder Visual C#-Konsolenanwendung in Visual Studio.

2. Öffnen der *Program.vb* oder *"Program.cs"* -Datei zur Bearbeitung, und fügen Sie den folgenden Code hinzu.

    ```vb
    Dim key As Microsoft.Win32.RegistryKey
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")
    key.SetValue("MyComputer", "Enabled")
    key.SetValue("LocalIntranet", "Enabled")
    key.SetValue("Internet", "Enabled")
    key.SetValue("TrustedSites", "Enabled")
    key.SetValue("UntrustedSites", "Disabled")
    key.Close()
    ```

    ```csharp
    Microsoft.Win32.RegistryKey key;
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");
    key.SetValue("MyComputer", "Enabled");
    key.SetValue("LocalIntranet", "Enabled");
    key.SetValue("Internet", "AuthenticodeRequired");
    key.SetValue("TrustedSites", "Enabled");
    key.SetValue("UntrustedSites", "Disabled");
    key.Close();
    ```

3. Erstellen Sie die Anwendung, und führen Sie sie aus.

## <a name="restrict-the-clickonce-trust-prompt"></a>Einschränken der ClickOnce-vertrauensaufforderung
 Schränken Sie die vertrauenswürdige Eingabeaufforderung aus, sodass Lösungen mit Authenticode-Zertifikaten signiert werden müssen, die Identität bekannt waren, bevor eine Entscheidung über die Vertrauenswürdigkeit abgefragt werden.

#### <a name="to-restrict-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Um die ClickOnce-vertrauensaufforderung zu beschränken, indem Sie den Registrierungs-editor

1. Öffnen Sie den Registrierungs-Editor ein:

    1. Klicken Sie auf **Start** und dann auf **Ausführen**.

    2. In der **öffnen** geben `regedit`, und klicken Sie dann auf **OK**.

2. Suchen Sie den folgenden Registrierungsschlüssel:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     Wenn der Schlüssel nicht vorhanden ist, erstellen Sie ihn aus.

3. Fügen Sie die folgenden Unterschlüssel als **Zeichenfolgenwert**, wenn sie nicht bereits mit den zugeordneten, in der folgenden Tabelle angezeigten Werten vorhanden sind.

    |Unterschlüssel für Zeichenfolge-Wert|Wert|
    |-------------------------|-----------|
    |`UntrustedSites`|`Disabled`|
    |`Internet`|`AuthenticodeRequired`|
    |`MyComputer`|`AuthenticodeRequired`|
    |`LocalIntranet`|`AuthenticodeRequired`|
    |`TrustedSites`|`AuthenticodeRequired`|

#### <a name="to-restrict-the-clickonce-trust-prompt-programmatically"></a>Um die ClickOnce-vertrauensaufforderung programmgesteuert zu beschränken.

1. Erstellen Sie eine Visual Basic oder Visual C#-Konsolenanwendung in Visual Studio.

2. Öffnen der *Program.vb* oder *"Program.cs"* -Datei zur Bearbeitung, und fügen Sie den folgenden Code hinzu.

    ```vb
    Dim key As Microsoft.Win32.RegistryKey
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")
    key.SetValue("MyComputer", "AuthenticodeRequired")
    key.SetValue("LocalIntranet", "AuthenticodeRequired")
    key.SetValue("Internet", "AuthenticodeRequired")
    key.SetValue("TrustedSites", "AuthenticodeRequired")
    key.SetValue("UntrustedSites", "Disabled")
    key.Close()
    ```

    ```csharp
    Microsoft.Win32.RegistryKey key;
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");
    key.SetValue("MyComputer", "AuthenticodeRequired");
    key.SetValue("LocalIntranet", "AuthenticodeRequired");
    key.SetValue("Internet", "AuthenticodeRequired");
    key.SetValue("TrustedSites", "AuthenticodeRequired");
    key.SetValue("UntrustedSites", "Disabled");
    key.Close();
    ```

3. Erstellen Sie die Anwendung, und führen Sie sie aus.

## <a name="disable-the-clickonce-trust-prompt"></a>Deaktivieren der ClickOnce-vertrauensaufforderung
 Sie können die vertrauenswürdige Eingabeaufforderung deaktivieren, damit Endbenutzer nicht erhalten, dass die Option zum Installieren von Lösungen, die bereits in ihrer Sicherheitsrichtlinie nicht vertraut wird.

#### <a name="to-disable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>So deaktivieren Sie die ClickOnce-vertrauensaufforderung mithilfe des Registrierungs-Editors

1. Öffnen Sie den Registrierungs-Editor ein:

    1. Klicken Sie auf **Start** und dann auf **Ausführen**.

    2. In der **öffnen** geben `regedit`, und klicken Sie dann auf **OK**.

2. Suchen Sie den folgenden Registrierungsschlüssel:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     Wenn der Schlüssel nicht vorhanden ist, erstellen Sie ihn aus.

3. Fügen Sie die folgenden Unterschlüssel als **Zeichenfolgenwert**, wenn sie nicht bereits mit den zugeordneten, in der folgenden Tabelle angezeigten Werten vorhanden sind.

    |Unterschlüssel für Zeichenfolge-Wert|Wert|
    |-------------------------|-----------|
    |`UntrustedSites`|`Disabled`|
    |`Internet`|`Disabled`|
    |`MyComputer`|`Disabled`|
    |`LocalIntranet`|`Disabled`|
    |`TrustedSites`|`Disabled`|

#### <a name="to-disable-the-clickonce-trust-prompt-programmatically"></a>So deaktivieren Sie die ClickOnce-vertrauensaufforderung programmgesteuert

1. Erstellen Sie eine Visual Basic oder Visual C#-Konsolenanwendung in Visual Studio.

2. Öffnen der *Program.vb* oder *"Program.cs"* -Datei zur Bearbeitung, und fügen Sie den folgenden Code hinzu.

    ```vb
    Dim key As Microsoft.Win32.RegistryKey
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")
    key.SetValue("MyComputer", "Disabled")
    key.SetValue("LocalIntranet", "Disabled")
    key.SetValue("Internet", "Disabled")
    key.SetValue("TrustedSites", "Disabled")
    key.SetValue("UntrustedSites", "Disabled")
    key.Close()
    ```

    ```csharp
    Microsoft.Win32.RegistryKey key;
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");
    key.SetValue("MyComputer", "Disabled");
    key.SetValue("LocalIntranet", "Disabled");
    key.SetValue("Internet", "Disabled");
    key.SetValue("TrustedSites", "Disabled");
    key.SetValue("UntrustedSites", "Disabled");
    key.Close();

    ```

3. Erstellen Sie die Anwendung, und führen Sie sie aus.

## <a name="see-also"></a>Siehe auch
- [Secure ClickOnce applications (Sichern von ClickOnce-Anwendungen)](../deployment/securing-clickonce-applications.md)
- [Codezugriffssicherheit für ClickOnce-Anwendungen](../deployment/code-access-security-for-clickonce-applications.md)
- [ClickOnce und Authenticode](../deployment/clickonce-and-authenticode.md)
- [Trusted application deployment overview (Überblick: Bereitstellen vertrauenswürdiger Anwendungen)](../deployment/trusted-application-deployment-overview.md)
- [Vorgehensweise: ClickOnce-Sicherheitseinstellungen aktivieren](../deployment/how-to-enable-clickonce-security-settings.md)
- [Vorgehensweise: Festlegen einer Sicherheitszone für eine ClickOnce-Anwendung](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Vorgehensweise: Festlegen Sie benutzerdefinierter Berechtigungen für eine ClickOnce-Anwendung](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Vorgehensweise: Debuggen einer ClickOnce-Anwendung mit eingeschränkten Berechtigungen](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)
- [Vorgehensweise: Hinzufügen eines vertrauenswürdigen Herausgebers auf einen Clientcomputer für ClickOnce-Anwendungen](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [Vorgehensweise: Erneutes Signieren von Anwendungs- und Bereitstellungsmanifesten](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
