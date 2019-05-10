---
title: Installieren von außerhalb des Ordners für Erweiterungen mit VSIX v3 | Microsoft-Dokumentation
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09b3b23a89450bb1abac4f8ebb10d00396a251b2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62433145"
---
# <a name="installing-outside-the-extensions-folder"></a>Installieren von außerhalb des Ordners für Erweiterungen

Beginnend mit Visual Studio 2017 und VSIX v3 (Version 3), unterstützt jetzt für die Installation der Erweiterung Ressourcen außerhalb der Ordner "Extensions". Derzeit werden die folgenden Speicherorte als gültige Installationsorte aktiviert (wobei die [INSTALLDIR] zum Installationsverzeichnis von Visual Studio-Instanz zugeordnet ist):

* [INSTALLDIR] \MSBuild
* [INSTALLDIR]\Xml\Schemas
* [INSTALLDIR]\Common7\IDE\PublicAssemblies
* [INSTALLDIR] \Licenses
* [INSTALLDIR]\Common7\IDE\ReferenceAssemblies
* [INSTALLDIR]\Common7\IDE\RemoteDebugger
* [INSTALLDIR]\Common7\IDE\VC\VCTargets

>**Hinweis**: Das VSIX-Format lässt nicht zu, dass Sie außerhalb der Ordnerstruktur des Visual Studio-Installation installieren.

Um auf diese Verzeichnisse installieren zu unterstützen, muss die VSIX-Datei installiert sein "pro pro-Computer-Instanz". Dies kann durch Aktivieren des Kontrollkästchens "alle Benutzer" im Designer "Extension.vsixmanifest" aktiviert werden:

![Überprüfen Sie alle Benutzer](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>Gewusst wie: Festlegen der InstallRoot

Um den Installationsverzeichnissen festzulegen, können Sie die **Eigenschaften** Fenster in Visual Studio. Sie können z. B. Festlegen der `InstallRoot` Eigenschaft einen Projektverweis auf einen der oben genannten Standorte:

![Installieren Sie die Root-Eigenschaften](media/install-root-properties.png)

Dadurch werden einige Metadaten hinzugefügt, mit der entsprechenden `ProjectReference` Eigenschaft innerhalb des VSIX-Projekts CSPROJ-Datei:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

>**Hinweis**: Sie können die CSPROJ-Datei direkt bearbeiten, falls gewünscht.

## <a name="how-to-set-a-subpath-under-the-installroot"></a>Wie Sie einen Unterpfad unter dem InstallRoot festlegen

Wenn Sie, um einen Unterpfad unter installieren möchten der `InstallRoot`, dazu können Sie festlegen der `VsixSubPath` Eigenschaft wie die `InstallRoot` Eigenschaft. Angenommen, wir möchten unsere Projektverweis-Ausgabe zu installieren "[INSTALLDIR]\MSBuild\MyCompany\MySDK\1.0". Dies ganz einfach mit dem Designer für die Eigenschaft ist möglich:

![Set-Unterpfad](media/set-subpath.png)

Die entsprechenden csproj-Änderungen werden wie folgt aussehen:

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>Zusätzliche Informationen

Der Designer Änderung der Eigenschaft gelten für mehr als nur-Projekt-verweisen. Sie können festlegen, die `InstallRoot` Metadaten für Elemente in Ihrem Projekt auch (mit der gleichen oben beschriebenen Methoden).
