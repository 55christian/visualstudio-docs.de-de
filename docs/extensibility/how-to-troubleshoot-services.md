---
title: 'Vorgehensweise: Problembehandlung bei Services | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 669b8880e3fe378b05cc258bf473d74d0e5401b6
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324814"
---
# <a name="how-to-troubleshoot-services"></a>Vorgehensweise: Problembehandlung bei Diensten
Es gibt einige häufige Probleme, die auftreten können, wenn Sie versuchen, einen Dienst zu erhalten:

- Der Dienst ist nicht registriert, mit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

- Der Dienst wird durch den Schnittstellentyp und nicht vom Dienst angefordert.

- Das VSPackage, das Anfordern des Diensts ist nicht positioniert wurde.

- Der falschen Dienst-Anbieter wird verwendet.

  Wenn der angeforderte Dienst kann nicht abgerufen werden, wird den Aufruf von <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> gibt null zurück. Sie sollten immer auf Null testen, nach dem Anfordern eines Diensts:

```csharp
IVsActivityLog log =
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="to-troubleshoot-a-service"></a>Problembehandlung für einen Dienst

1. Überprüfen Sie die systemregistrierung, um festzustellen, ob der Dienst ordnungsgemäß registriert wurde. Weitere Informationen finden Sie unter [Vorgehensweise: Geben Sie einen Dienst](../extensibility/how-to-provide-a-service.md).

    Die folgenden *reg* Dateifragment zeigt, wie der SVsTextManager-Dienst registriert werden kann:

   ```
   [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]
   @="{F5E7E720-1401-11d1-883B-0000F87579D2}"
   "Name"="SVsTextManager"
   ```

    Im obigen Beispiel ist die Versionsnummer die Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], z. B. 12.0 oder 14.0, den Schlüssel {F5E7E71D-1401-11d1-883B-0000F87579D2} ist die Dienst-ID (SID) der Dienst, SVsTextManager und den standardmäßigen Wert {} F5E7E720-1401-11D1-883B-0000F87579D2} ist die Paket-GUID des TextManager-VSPackage, das den Dienst bereitstellt.

2. Verwenden Sie den Diensttyp und nicht den Schnittstellentyp, beim Aufrufen von "GetService". Beim Anfordern eines Diensts von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], <xref:Microsoft.VisualStudio.Shell.Package> extrahiert die GUID aus dem Typ. Ein Dienst wird nicht gefunden werden, wenn die folgenden Bedingungen erfüllt sein:

   1. Ein Schnittstellentyp ist "GetService" anstelle der Diensttyp übergeben.

   2. Die Schnittstelle ist explizit keine GUID zugewiesen. Daher erstellt das System einen Standard-GUID für ein Objekt nach Bedarf.

3. Achten Sie darauf, dass das VSPackage, die die Dienste anfordern positioniert wurde. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] eine VSPackage Standorten, nach dem Erstellen es und vor dem Aufruf <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>.

    Wenn Sie Code in einem VSPackage-Konstruktor verfügen, die ein Dienst benötigt, verschieben sie Sie der `Initialize` Methode.

4. Achten Sie darauf, dass Sie den richtigen Service-Anbieter verwenden.

    Nicht alle Dienstanbieter sind. Der Dienstanbieter, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] übergibt zu einem Toolfenster unterscheidet sich von der zu einer VSPackage übergibt. Der Dienstanbieter der Tool-Fenster kennt <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>, aber nicht kennt <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. Rufen Sie <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> um ein VSPackage-Dienstanbieter aus in einem Toolfenster zu erhalten.

    Wenn ein Toolfenster ein Benutzersteuerelement oder einem anderen Steuerelementcontainer hostet, wird der Container wird vom Windows-Komponentenmodell positioniert werden und haben keinen Zugriff auf alle [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Dienste. Rufen Sie <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> um ein VSPackage-Dienstanbieter aus in einem Steuerelementcontainers zu erhalten.

## <a name="see-also"></a>Siehe auch
- [Liste der verfügbaren Dienste](../extensibility/internals/list-of-available-services.md)
- [Verwenden und Dienste bereitstellen](../extensibility/using-and-providing-services.md)
- [Dienstgrundlagen](../extensibility/internals/service-essentials.md)