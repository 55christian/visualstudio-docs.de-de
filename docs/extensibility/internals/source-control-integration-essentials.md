---
title: Grundlagen der Integration der Datenquelle | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 16c785534b843977f28c9a1383ac93f33e216947
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62908950"
---
# <a name="source-control-integration-essentials"></a>Grundlagen der Integration der Quellcodeverwaltung
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] unterstützt zwei Arten der Integration der quellcodeverwaltung: ein Quellcodeverwaltungs-Plug-Ins, die stellt grundlegende Funktionalität bereit und wird mithilfe der Quell-Plug-in-API (ehemals die MSSCCI-API) und eine VSPackage-basierten Datenquellen-Steuerelement-integrationslösung erstellt, Stellt robuster Funktionen bereit.

## <a name="source-control-plug-in"></a>Quellcodeverwaltung-Plug-in
 Ein Datenquellen-Steuerelement-Plug-in wird als DLL geschrieben, die die Source-Plug-in-API implementiert. Registrierung und Datenquellen-Steuerelement-Integration-Funktionalität wird über die API bereitgestellt. Dieser Ansatz ist einfacher zu implementieren als ein Quellcodeverwaltungs-VSPackage und verwendet die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Benutzeroberfläche (UI) für die meisten Quellcodeverwaltungsvorgänge.

 Gehen Sie folgendermaßen vor, um ein Quellcodeverwaltungs-Plug-in mit der Source-Plug-in-API zu implementieren:

1. Erstellen Sie eine DLL, die die angegebenen Funktionen implementiert [Quellcodeverwaltung-Plug-ins](../../extensibility/source-control-plug-ins.md).

2. Registrieren Sie die DLL, indem Sie die entsprechenden Registrierungseinträge, machen, wie in beschrieben [Vorgehensweise: Installieren eines Quellcodeverwaltungs-Plug-in](../../extensibility/internals/how-to-install-a-source-control-plug-in.md).

3. Erstellen Sie eine Hilfsprogramm-UI und Aufforderung durch den Adapter Quellcodeverwaltungspaket anzeigen (die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] -Komponente, die Quellcodeverwaltungsfunktionen über den Quellcodeverwaltungs-Plug-ins behandelt).

   Weitere Informationen finden Sie unter [ein Datenquellen-Steuerelement-Plug-in erstellen](../../extensibility/internals/creating-a-source-control-plug-in.md).

## <a name="source-control-vspackage"></a>Quellcodeverwaltungs-VSPackage
 Ein Quellcodeverwaltungs-VSPackage-Implementierung können Sie zum Entwickeln von benutzerdefinierten Ersatz für die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Datenquellen-Steuerelement-Benutzeroberfläche. Dieser Ansatz bietet vollständige Kontrolle über die Integration der quellcodeverwaltung, aber es erfordert, dass Sie die Elemente der Benutzeroberfläche bereitstellen und implementieren Sie die Steuerelement-Schnittstellen, die unter der-Plug-in-Ansatz bereitgestellt werden. Andernfalls würde.

 Um ein Quellcodeverwaltungs-VSPackage implementieren zu können, müssen Sie folgende Aktionen ausführen:

1. Erstellen und registrieren Sie Ihrer eigenen quellcodeverwaltung VSPackage, siehe [Registrierung und Auswahl](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).

2. Ersetzen Sie die Standard-quellcodeverwaltung Benutzeroberfläche, durch die benutzerdefinierte Benutzeroberfläche. Finden Sie unter [benutzerdefinierte Benutzeroberfläche](../../extensibility/internals/custom-user-interface-source-control-vspackage.md).

3. Geben Sie die Symbole verwendet werden, und das behandeln **Projektmappen-Explorer** Symbol-Ereignisse. Finden Sie unter [Glyphensteuerung](../../extensibility/internals/glyph-control-source-control-vspackage.md).

4. Abfrage bearbeiten und speichern Sie die Abfrage Ereignisse behandeln, siehe [Abfrage bearbeiten die Abfrage speichern](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md).

   Weitere Informationen finden Sie unter [Erstellen eines Quellcodeverwaltungs-VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md).

## <a name="see-also"></a>Siehe auch
- [Übersicht](../../extensibility/internals/source-control-integration-overview.md)
- [Erstellen eines Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [Erstellen eines Quellcodeverwaltungs-VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)