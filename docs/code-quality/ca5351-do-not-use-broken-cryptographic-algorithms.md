---
title: CA5351 Verwenden Sie keine unterbrochenen kryptografischen Algorithmen.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 483f51b3-e186-4433-b48e-5ca24a9a9c94
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f9af307158ecd8d5a1f93ebd1f8575cad5cf51e5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62540858"
---
# <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a>CA5351 Verwenden Sie keine unterbrochenen kryptografischen Algorithmen.

|||
|-|-|
|TypeName|DoNotUseBrokenCryptographicAlgorithms|
|CheckId|CA5351|
|Kategorie|Microsoft.Cryptography|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

> [!NOTE]
> Diese Warnung wurde zuletzt im November 2015 aktualisiert.

## <a name="cause"></a>Ursache

Hashfunktionen wie <xref:System.Security.Cryptography.MD5> und Verschlüsselungsalgorithmen wie <xref:System.Security.Cryptography.DES> und <xref:System.Security.Cryptography.RC2> können ein erhebliches Risiko darstellen und führen möglicherweise zur Enthüllung vertraulicher Informationen mithilfe einfacher Angriffsstrategien, wie z. B. Brute-Force-Angriffe und Kollisionsangriffe gegen Hashfunktionen.

Die kryptografischen Algorithmen in der folgenden Liste sind anfällig für bekannte kryptografische Angriffe. Der kryptografische Hashalgorithmus <xref:System.Security.Cryptography.MD5> ist anfällig für Kollisionsangriffe gegen Hashfunktionen.  Je nach Einsatzbereich führen Kollisionsangriffe gegen Hashfunktionen zu Identitätswechseln, Manipulationen oder anderen Arten von Angriffen auf Systeme, die auf der eindeutigen kryptografischen Ausgabe einer Hashfunktion beruhen. Die Verschlüsselungsalgorithmen <xref:System.Security.Cryptography.DES> und <xref:System.Security.Cryptography.RC2> sind anfällig für kryptografische Angriffe, die zu einer unbeabsichtigten Offenlegung von verschlüsselten Daten führen können.

## <a name="rule-description"></a>Regelbeschreibung

Unterbrochene kryptografische Algorithmen werden nicht als sicher betrachtet; ihre Verwendung sollte unterbunden werden. Der MD5-Hashalgorithmus ist anfällig für bekannte Kollisionsangriffe. Die spezielle Sicherheitslücke hängt jedoch vom Verwendungszusammenhang ab.  Zum Sicherstellen der Datenintegrität (z. B. Dateisignatur oder digitales Zertifikat) verwendete Hashalgorithmen sind besonders anfällig.  In diesem Kontext könnten Angreifer zwei separate Teile der Daten generieren und nützliche Daten durch schädliche Daten ersetzen, ohne den Hashwert zu ändern oder eine zugeordnete digitale Signatur für ungültig zu erklären.

Bei Verschlüsselungsalgorithmen:

- Die<xref:System.Security.Cryptography.DES> -Verschlüsselung enthält eine kleine Schlüsselgröße, die in weniger als einem Tag einem Brute-Force-Angriff zum Opfer fallen könnte.

- Die<xref:System.Security.Cryptography.RC2> -Verschlüsselung ist anfällig für einen schlüsselbezogenen Angriff, bei dem der Angreifer nach mathematischen Beziehungen zwischen allen Schlüsselwerten sucht.

Diese Regel löst aus, wenn eine der oben genannten Kryptografiefunktionen im Quellcode gefunden wird, und gibt eine Warnung für den Benutzer aus.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Verwenden Sie kryptografisch sicherere Optionen:

- Verwenden Sie für MD5 Hashes der [SHA-2](/windows/desktop/SecCrypto/hash-and-signature-algorithms) -Produktfamilie (z. B. <xref:System.Security.Cryptography.SHA512>, <xref:System.Security.Cryptography.SHA384>, <xref:System.Security.Cryptography.SHA256>).

- Verwenden Sie für DES und RC2 eine <xref:System.Security.Cryptography.Aes> -Verschlüsselung.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Unterdrücken Sie keine Warnung dieser Regel, bevor sie von einem Kryptografie-Experten geprüft wurde.

## <a name="pseudo-code-examples"></a>Pseudocodebeispiele

Die folgenden Pseudocode-Beispiele veranschaulichen das von dieser Regel und mögliche Alternativen erkannte Muster.

### <a name="md5-hashing-violation"></a>Verstoß bei MD5-Hashfunktion

```csharp
using System.Security.Cryptography;
...
var hashAlg = MD5.Create();
```

Projektmappe:

```csharp
using System.Security.Cryptography;
...
var hashAlg = SHA256.Create();
```

### <a name="rc2-encryption-violation"></a>Verstoß bei RC2-Verschlüsselung

```csharp
using System.Security.Cryptography;
...
RC2 encAlg = RC2.Create();
```

Projektmappe:

```csharp
using System.Security.Cryptography;
...
using (AesManaged encAlg = new AesManaged())
{
  ...
}
```

### <a name="des-encryption-violation"></a>Verstoß bei DES-Verschlüsselung

```csharp
using System.Security.Cryptography;
...
DES encAlg = DES.Create();
```

Projektmappe:

```csharp
using System.Security.Cryptography;
...
using (AesManaged encAlg = new AesManaged())
{
  ...
}
```