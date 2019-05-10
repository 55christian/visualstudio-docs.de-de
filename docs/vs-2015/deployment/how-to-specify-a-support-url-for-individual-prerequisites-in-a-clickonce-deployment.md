---
title: 'Vorgehensweise: Angeben eines Support-URLs für einzelne erforderliche Komponenten in einer ClickOnce-Bereitstellung | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, prerequisites
- ClickOnce deployment, URLs
ms.assetid: 590742c3-a286-4160-aa75-7a441bb2207b
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f272f1b7a8fc970ab616ba1c02e815cbb6ecb568
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60059135"
---
# <a name="how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment"></a>Vorgehensweise: Angeben eines Support-URLs für einzelne erforderliche Komponenten in einer ClickOnce-Bereitstellung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ein [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Testen der Bereitstellung können Sie für eine Reihe von Voraussetzungen, die auf dem Clientcomputer für verfügbar sein müssen die [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung ausgeführt. Dazu gehören die erforderliche Mindestversion von der [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], die Version des Betriebssystems und alle Assemblys, die im globalen Assemblycache (GAC) vorinstalliert sein müssen. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], kann jedoch nicht installiert diese erforderlichen Komponenten selbst Wenn eine erforderliche Komponente nicht gefunden wird, wird die Installation angehalten es einfach an und zeigt ein Dialogfeld, die erläutern, warum Fehler bei der Installation an.  
  
 Es gibt zwei Methoden zum Installieren der erforderlichen Komponenten. Sie können sie mit der eine Bootstrapper-Anwendung installieren. Alternativ können Sie eine Support-URL für einzelne erforderliche Komponenten angeben, die für Benutzer im Dialogfeld angezeigt wird, wenn die erforderliche Komponente nicht gefunden wird. Die Seite, die auf diese URL verweist, kann Links zu Anweisungen zum Installieren der erforderlichen Komponente enthalten. Wenn eine Anwendung eine Support-URL für eine einzelne erforderliche Komponente, nicht angeben, wird [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] zeigt die Support-URL in das Bereitstellungsmanifest für die Anwendung als Ganzes angegeben, wenn er definiert ist.  
  
 Während [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], Mage.exe und MageUI.exe können alle verwendet werden, generieren [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Bereitstellungen keines dieser Tools direkt unterstützt eine Support-URL für einzelne erforderliche Komponenten angeben. In diesem Dokument wird beschrieben, wie so ändern Sie der Bereitstellung des Anwendungs- und Bereitstellungsmanifest, dazu gehören support-URLs.  
  
### <a name="specifying-a-support-url-for-an-individual-prerequisite"></a>Angeben eines Support-URLs für eine einzelne erforderliche Komponente  
  
1. Öffnen Sie das Anwendungsmanifest (die Manifest-Datei) für Ihre [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] -Anwendung in einem Text-Editor.  
  
2. Für ein erforderliches Betriebssystem hinzufügen der `supportUrl` -Attribut auf die `dependentOS` Element:  
  
    ```  
     <dependency>  
        <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">  
          <osVersionInfo>  
            <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />  
          </osVersionInfo>  
        </dependentOS>  
      </dependency>  
    ```  
  
3. Für eine Voraussetzung für eine bestimmte Version der common Language Runtime, Hinzufügen der `supportUrl` -Attribut auf die `dependentAssembly` Eintrag, der angibt, die common Language Runtime-Abhängigkeit:  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">  
          <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
4. Legen Sie für eine Voraussetzung für eine Assembly, die im globalen Assemblycache vorinstalliert sein muss, die `supportUrl` für die `dependentAssembly` Element, das die erforderliche Assembly angibt:  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">  
          <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
5. Dies ist optional. Für Anwendungen, die .NET Framework 4, öffnen Sie das Bereitstellungsmanifest (die Application-Datei) für Ihre [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] -Anwendung in einem Text-Editor.  
  
6. Voraussetzung für .NET Framework 4, Hinzufügen der `supportUrl` -Attribut auf die `compatibleFrameworks` Element:  
  
    ```  
    <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">  
      <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />  
      <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />  
    </compatibleFrameworks>  
    ```  
  
7. Nachdem Sie das Anwendungsmanifest manuell geändert haben, müssen Sie erneut das Anwendungsmanifest, das mit Ihrer digitalen Zertifikat signieren und dann aktualisieren und erneut signieren sowie das Bereitstellungsmanifest. Verwenden Sie Mage.exe oder MageUI.exe SDK-tools zum Ausführen dieser Aufgabe, als diese Dateien mithilfe von Neugenerieren [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] manuellen Änderungen löscht. Weitere Informationen zur Verwendung von Mage.exe zum erneuten Signieren von Manifesten finden Sie unter [Vorgehensweise: Erneutes Signieren von Anwendungs- und Bereitstellungsmanifeste](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## <a name="net-framework-security"></a>.NET Framework-Sicherheit  
 Die Support-URL wird nicht im Dialogfeld angezeigt, wenn die Anwendung für die Ausführung unter teilweiser Vertrauenswürdigkeit markiert ist.  
  
## <a name="see-also"></a>Siehe auch  
 [„Mage.exe“ (Tool zum Generieren und Bearbeiten von Manifesten)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [\<CompatibleFrameworks >-Element](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [ClickOnce und Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Vorbedingungen für die Anwendungsbereitstellung](../deployment/application-deployment-prerequisites.md)
