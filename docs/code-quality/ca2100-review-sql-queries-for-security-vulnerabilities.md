---
title: 'CA2100: SQL-Abfragen auf Sicherheitsrisiken überprüfen.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Review SQL queries for security vulnerabilities
- ReviewSqlQueriesForSecurityVulnerabilities
- CA2100
helpviewer_keywords:
- CA2100
- ReviewSqlQueriesForSecurityVulnerabilities
ms.assetid: 79670604-c02a-448d-9c0e-7ea0120bc5fe
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: b3ba92e154e3091f6ec483ba469c3fe60f50ec61
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66744805"
---
# <a name="ca2100-review-sql-queries-for-security-vulnerabilities"></a>CA2100: SQL-Abfragen auf Sicherheitsrisiken überprüfen.

|||
|-|-|
|TypeName|ReviewSqlQueriesForSecurityVulnerabilities|
|CheckId|CA2100|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Eine Methode legt die <xref:System.Data.IDbCommand.CommandText%2A?displayProperty=fullName> Eigenschaft mithilfe einer Zeichenfolge, die aus einem Zeichenfolgenargument für die Methode erstellt wird.

## <a name="rule-description"></a>Regelbeschreibung

Diese Regel setzt voraus, dass das Zeichenfolgenargument Benutzereingaben enthält. Eine aus Benutzereingaben erstellte SQL-Befehlszeichenfolge ist anfällig für SQL-Injection-Angriffe. In einer SQL-Injection-Angriff stellt ein böswilliger Benutzer Eingaben, die den Entwurf einer Abfrage zu beschädigen oder damit unautorisierter Zugriff auf die zugrunde liegende Datenbank ändert. Typische Techniken sind die Einfügung von einem einzelnen Anführungszeichen oder Apostroph, die die SQL-Zeichenfolgenliteral-Trennzeichen ist: zwei Gedankenstriche, was bedeutet einen SQL-Kommentar; und ein Semikolon, was bedeutet, dass ein neuer Befehl folgt. Wenn der Benutzereingabe Teil der Abfrage, verwenden Sie eine der folgenden sein muss aufgeführt, in der Reihenfolge der Effektivität, um das Risiko von Angriffen zu verringern.

- Verwenden Sie eine gespeicherte Prozedur.

- Verwenden Sie eine parametrisierten Befehl-Zeichenfolge.

- Überprüfen Sie die Benutzereingabe für Typ und Inhalt vor dem Erstellen der Befehlszeichenfolge.

Implementieren Sie die folgenden Typen von .NET die <xref:System.Data.IDbCommand.CommandText%2A> Eigenschaft oder Konstruktoren, die die Eigenschaft festgelegt wird, mit der ein Zeichenfolgenargument bereitstellen.

- <xref:System.Data.Odbc.OdbcCommand?displayProperty=fullName> und <xref:System.Data.Odbc.OdbcDataAdapter?displayProperty=fullName>

- <xref:System.Data.OleDb.OleDbCommand?displayProperty=fullName> und <xref:System.Data.OleDb.OleDbDataAdapter?displayProperty=fullName>

- <xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName> und <xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>

- <xref:System.Data.SqlClient.SqlCommand?displayProperty=fullName> und <xref:System.Data.SqlClient.SqlDataAdapter?displayProperty=fullName>

Beachten Sie, dass diese Regel verletzt wird, wenn die ToString-Methode eines Typs explizit oder implizit verwendet wird, die die Abfragezeichenfolge zu erstellen. Nachfolgend finden Sie ein Beispiel:

```csharp
int x = 10;
string query = "SELECT TOP " + x.ToString() + " FROM Table";
```

Die Regel wird verletzt, da ein böswilliger Benutzer die ToString()-Methode überschreiben kann.

Die Regel wird auch verletzt werden, wenn ToString implizit verwendet wird.

```csharp
int x = 10;
string query = String.Format("SELECT TOP {0} FROM Table", x);
```

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, verwenden Sie eine parametrisierte Abfrage ein.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Es ist sicher eine Warnung dieser Regel zu unterdrücken, wenn der Befehlstext keine Benutzereingaben.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt eine Methode, `UnsafeQuery`, die gegen die Regel und eine Methode, `SaferQuery`, der Regel mithilfe einer parametrisierten Befehlszeichenfolge entspricht.

[!code-vb[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/VisualBasic/ca2100-review-sql-queries-for-security-vulnerabilities_1.vb)]
[!code-csharp[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CSharp/ca2100-review-sql-queries-for-security-vulnerabilities_1.cs)]
[!code-cpp[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CPP/ca2100-review-sql-queries-for-security-vulnerabilities_1.cpp)]

## <a name="see-also"></a>Siehe auch

- [Übersicht über die Sicherheit](/dotnet/framework/data/adonet/security-overview)