---
title: '&lt;PublisherIdentity&gt; -Element (ClickOnce-Bereitstellung) | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publisherIdentity Element [ClickOnce deployment manifest], introduction
- required element for signed manifests [ClickOnce], publisherIdentity Element
- publisherIdentity Element [ClickOnce deployment manifest], syntax, elements, and attributes
ms.assetid: 34c579db-d2f2-4b66-b9c8-47207f33d950
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 995b002784c1e76ceed36e51edb1ae893448f448
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62927538"
---
# <a name="ltpublisheridentitygt-element-clickonce-deployment"></a>&lt;PublisherIdentity&gt; -Element (ClickOnce-Bereitstellung)
Enthält Informationen zum Herausgeber, der dieses Bereitstellungsmanifest signiert hat.

## <a name="syntax"></a>Syntax

```xml
<publisherIdentity
   name
   issuerKeyHash
/>
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Die `publisherIdentity` Element für signierte Manifeste erforderlich ist. Die folgende Tabelle zeigt die Attribute an, dass die `publisherIdentity` Element unterstützt.

|Attribut|Beschreibung|
|---------------|-----------------|
|`name`|Erforderlich. Beschreibt die Identität der Partei, die diese Anwendung veröffentlicht.|
|`issuerKeyHash`|Erforderlich. Enthält den SHA-1-Hash des öffentlichen Schlüssels des Zertifikatausstellers.|

#### <a name="parameters"></a>Parameter

## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert

## <a name="exceptions"></a>Ausnahmen

## <a name="remarks"></a>Hinweise

## <a name="requirements"></a>Anforderungen

## <a name="subhead"></a>Untertitel