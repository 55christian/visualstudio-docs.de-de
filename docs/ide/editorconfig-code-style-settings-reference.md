---
title: Einstellungen für die .NET-Codierungskonventionen für EditorConfig
ms.date: 06/14/2018
ms.topic: reference
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- coding conventions [EditorConfig]
- EditorConfig coding conventions
- language code style rules [EditorConfig]
- formatting conventions [EditorConfig]
author: kuhlenh
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3cdd9f0b46c578f713b7f2af2940f4d7742df19a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62557215"
---
# <a name="net-coding-convention-settings-for-editorconfig"></a>Einstellungen für die .NET-Codierungskonventionen für „EditorConfig“

Sie können in Ihrer Codebasis das Codeformat mit einer [EditorConfig](../ide/create-portable-custom-editor-options.md)-Datei definieren und verwalten. „EditorConfig“ enthält mehrere wesentliche Formatierungseigenschaften, wie z.B. `indent_style` und `indent_size`. In Visual Studio können Einstellungen für die .NET-Codierungskonventionen auch mit einer EditorConfig-Datei konfiguriert werden. Sie können einzelne .NET-Codierungskonventionen aktivieren oder deaktivieren und konfigurieren, inwieweit die einzelnen Regeln über einen Schweregrad erzwungen werden sollen.

> [!TIP]
> - Wenn Sie Codierungskonventionen in einer EDITORCONFIG-Datei definieren, konfigurieren Sie damit, wie die in Visual Studio integrierten [Codestil-Analysetools](../code-quality/roslyn-analyzers-overview.md) Ihren Code analysieren sollen. Die EDITORCONFIG-Datei ist die Konfigurationsdatei für diese Analysetools.
> - Codeformateinstellungen für Visual Studio können auch im Dialogfeld mit den [Text-Editor-Optionen](code-styles-and-quick-actions.md) festgelegt werden. Die Einstellungen in der EDITORCONFIG-Datei haben Vorrang, und unter **Optionen** festgelegte Einstellungen sind keinem bestimmten Projekt zugeordnet.

Am Ende dieses Artikels finden Sie ein [Beispiel für eine EDITORCONFIG-Datei](#example-editorconfig-file).

## <a name="convention-categories"></a>Kategorien für Konventionen

Es gibt drei unterstützte Kategorien für .NET-Codierungskonventionen:

- [Sprachcodeformate](#language-code-styles)

   Regeln für die Sprache C# oder die Sprache Visual Basic. Beispielsweise können Sie Regeln hinsichtlich der Verwendung von `var` oder explizite Typen angeben, wenn Sie Variablen definieren oder Ausdruckskörpermember bevorzugen.

- [Formatierungskonventionen](#formatting-conventions)

   Regeln für das Layout und die Struktur Ihres Codes, um diesen lesbarer zu machen. Beispielsweise können Sie Regeln hinsichtlich der geschweiften Klammern (Allman) angeben, oder es werden Leerzeichen in Steuerblöcken bevorzugt.

- [Namenskonventionen](../ide/editorconfig-naming-conventions.md)

   Regeln für die Benennung von Codeelementen. Sie können beispielsweise angeben, dass die `async`-Methoden mit „Async“ enden müssen.

## <a name="language-code-styles"></a>Sprachcodeformate

Regeln für die Sprachcodeformate weisen folgendes Format auf:

`options_name = false|true : none|silent|suggestion|warning|error`

Für jedes Sprachcodeformat müssen Sie entweder **TRUE** (dieses Format wird bevorzugt) oder **FALSE** (dieses Format wird nicht bevorzugt) und einen **Schweregrad** angeben. Der Schweregrad gibt die Ebene der Erzwingung für dieses Format an.

In der folgenden Tabelle werden die möglichen Schweregrade und die zugehörigen Auswirkungen aufgeführt:

Schweregrad | Effekt
:------- | ------
`none` | Zeigen Sie dem Benutzer nichts mehr an, wenn gegen diese Regel verstoßen wird. Features zur Codegenerierung generieren jedoch Code in diesem Format. Regeln mit dem Schweregrad `none` werden im Menü **Schnelle Aktionen und Refactorings** nie angezeigt. In den meisten Fällen gelten diese als „deaktiviert“ oder „ignoriert“.
`silent` (auch `refactoring` in Visual Studio 2017-Version 15.8) | Zeigen Sie dem Benutzer nichts mehr an, wenn gegen diese Regel verstoßen wird. Features zur Codegenerierung generieren jedoch Code in diesem Format. Regeln mit dem Schweregrad `silent` gelten für Bereinigungsvorgänge und werden im Menü **Schnellaktionen und Refactorings** angezeigt.
`suggestion` | Wenn gegen diese Regel verstoßen wird, zeigen Sie sie dem Benutzer als Vorschlag an. Vorschläge werden in Form von drei grauen Punkten unter den ersten zwei Zeichen dargestellt.
`warning` | Zeigen Sie eine Compilerwarnung an, wenn gegen diese Formatregel verstoßen wird.
`error` | Zeigen Sie einen Compilerfehler an, wenn gegen diese Formatregel verstoßen wird.

Die folgende Liste enthält die zulässigen Einstellungen für Sprachcodeformate:

- Einstellungen für das .NET-Codeformat
    - [Qualifizierer „This.“ und „Me.“](#this_and_me)
        - dotnet\_style\_qualification\_for_field
        - dotnet\_style\_qualification\_for_property
        - dotnet\_style\_qualification\_for_method
        - dotnet\_style\_qualification\_for_event
    - [Sprachschlüsselwörter anstelle von Framework-Typnamen für Typverweise](#language_keywords)
        - dotnet\_style\_predefined\_type\_for\_locals\_parameters_members
        - dotnet\_style\_predefined\_type\_for\_member_access
    - [Einstellungen von Modifizierern](#normalize_modifiers)
        - dotnet\_style\_require\_accessibility_modifiers
        - csharp\_preferred\_modifier_order
        - visual\_basic\_preferred\_modifier_order
        - dotnet\_style\_readonly\_field
    - [Einstellungen für Klammern](#parentheses)
        - dotnet\_style\_parentheses\_in\_arithmetic\_binary\_operators
        - dotnet\_style\_parentheses\_in\_other\_binary\_operators
        - dotnet\_style\_parentheses\_in\_other\_operators
        - dotnet\_style\_parentheses\_in\_relational\_binary\_operators
    - [Einstellungen auf Ausdrucksebene](#expression_level)
        - dotnet\_style\_object_initializer
        - dotnet\_style\_collection_initializer
        - dotnet\_style\_explicit\_tuple_names
        - dotnet\_style\_prefer\_inferred\_tuple_names
        - dotnet\_style\_prefer\_inferred\_anonymous\_type\_member_names
        - dotnet\_style\_prefer\_auto\_properties
        - dotnet\_style\_prefer\_is\_null\_check\_over\_reference\_equality\_method
        - dotnet\_style\_prefer\_conditional\_expression\_over\_assignment
        - dotnet\_style\_prefer\_conditional\_expression\_over\_return
    - [Einstellungen für die NULL-Überprüfung](#null_checking)
        - dotnet\_style\_coalesce_expression
        - dotnet\_style\_null_propagation
- Einstellungen für das C#-Codeformat
    - [Implizite und explizite Typen](#implicit-and-explicit-types)
        - csharp\_style\_var\_for\_built\_in_types
        - csharp\_style\_var\_when\_type\_is_apparent
        - csharp\_style\_var_elsewhere
    - [Ausdruckskörpermember](#expression_bodied_members)
        - csharp\_style\_expression\_bodied_methods
        - csharp\_style\_expression\_bodied_constructors
        - csharp\_style\_expression\_bodied_operators
        - csharp\_style\_expression\_bodied_properties
        - csharp\_style\_expression\_bodied_indexers
        - csharp\_style\_expression\_bodied_accessors
    - [Mustervergleich](#pattern_matching)
        - csharp\_style\_pattern\_matching\_over\_is\_with\_cast_check
        - csharp\_style\_pattern\_matching\_over\_as\_with\_null_check
    - [Inline-Variablendeklarationen](#inlined_variable_declarations)
        - csharp\_style\_inlined\_variable_declaration
    - [Einstellungen auf Ausdrucksebene](#expression_level_csharp)
        - csharp\_prefer\_simple\_default_expression
        - csharp\_style\_deconstructed\_variable_declaration
        - csharp\_style\_pattern\_local\_over\_anonymous_function
    - [Einstellungen für die NULL-Überprüfung](#null_checking_csharp)
        - csharp\_style\_throw_expression
        - csharp\_style\_conditional\_delegate_call
    - [Codeblockeinstellungen](#code_block)
        - csharp\_prefer_braces

### <a name="net-code-style-settings"></a>Einstellungen für das .NET-Codeformat

Die Formatregeln in diesem Abschnitt gelten für C# und für Visual Basic. Wenn Sie Codebeispiele in Ihrer bevorzugten Programmiersprache anzeigen möchten, wählen Sie diese in der oberen rechten Ecke Ihres Browserfensters im Dropdownmenü **Sprache** aus.

#### <a name="this_and_me"></a>Die Qualifizierer „This.“ und „Me.“

Diese Formatregel (Regel-IDs IDE0003 und IDE0009) kann auf Felder, Eigenschaften, Methoden oder Ereignisse angewendet werden. Wenn **TRUE** festgelegt ist, wird dem Codesymbol in C# bevorzugt `this.` oder in Visual Basic `Me.` vorangestellt. Wenn **FALSE** festgelegt ist, wird dem Codeelement bevorzugt _nicht_ `this.` oder `Me.` vorangestellt.

Die folgende Tabelle zeigt die Regelnamen, gültigen Programmiersprachen und Standardwerte:

| Regelname | Anzuwendende Sprachen | Visual Studio-Standardwert |
| ----------- | -------------------- | ----------------------|
| dotnet_style_qualification_for_field | C# und Visual Basic | false:silent |
| dotnet_style_qualification_for_property | C# und Visual Basic | false:silent |
| dotnet_style_qualification_for_method | C# und Visual Basic | false:silent |
| dotnet_style_qualification_for_event | C# und Visual Basic | false:silent |

**dotnet\_style\_qualification\_for_field**

- Wenn diese Regel auf **TRUE** festgelegt ist, wird Feldern in C# bevorzugt `this.` oder in Visual Basic `Me.` vorangestellt.
- Wenn diese Regel auf **FALSE** festgelegt ist, wird Feldern bevorzugt _nicht_ `this.` oder `Me.` vorangestellt.

Codebeispiele:

```csharp
// dotnet_style_qualification_for_field = true
this.capacity = 0;

// dotnet_style_qualification_for_field = false
capacity = 0;
```

```vb
' dotnet_style_qualification_for_field = true
Me.capacity = 0

' dotnet_style_qualification_for_field = false
capacity = 0
```

**dotnet\_style\_qualification\_for_property**

- Wenn diese Regel auf **TRUE** festgelegt ist, wird Eigenschaften in C# bevorzugt `this.` oder in Visual Basic `Me.` vorangestellt.
- Wenn diese Regel auf **FALSE** festgelegt ist, wird Eigenschaften bevorzugt _nicht_ `this.` oder `Me.` vorangestellt.

Codebeispiele:

```csharp
// dotnet_style_qualification_for_property = true
this.ID = 0;

// dotnet_style_qualification_for_property = false
ID = 0;
```

```vb
' dotnet_style_qualification_for_property = true
Me.ID = 0

' dotnet_style_qualification_for_property = false
ID = 0
```

**dotnet\_style\_qualification\_for_method**

- Wenn diese Regel auf **TRUE** festgelegt ist, wird Methoden in C# bevorzugt `this.` oder in Visual Basic `Me.` vorangestellt.
- Wenn diese Regel auf **FALSE** festgelegt ist, wird Methoden bevorzugt _nicht_ `this.` oder `Me.` vorangestellt.

Codebeispiele:

```csharp
// dotnet_style_qualification_for_method = true
this.Display();

// dotnet_style_qualification_for_method = false
Display();
```

```vb
' dotnet_style_qualification_for_method = true
Me.Display()

' dotnet_style_qualification_for_method = false
Display()
```

**dotnet\_style\_qualification\_for_event**

- Wenn diese Regel auf **TRUE** festgelegt ist, wird Ereignissen in C# bevorzugt `this.` oder in Visual Basic `Me.` vorangestellt.
- Wenn diese Regel auf **FALSE** festgelegt ist, wird Ereignissen bevorzugt _nicht_ `this.` oder `Me.` vorangestellt.

Codebeispiele:

```csharp
// dotnet_style_qualification_for_event = true
this.Elapsed += Handler;

// dotnet_style_qualification_for_event = false
Elapsed += Handler;
```

```vb
' dotnet_style_qualification_for_event = true
AddHandler Me.Elapsed, AddressOf Handler

' dotnet_style_qualification_for_event = false
AddHandler Elapsed, AddressOf Handler
```

Diese Regeln werden in einer *EDITORCONFIG-Datei* z.B. folgendermaßen angezeigt:

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_qualification_for_field = false:suggestion
dotnet_style_qualification_for_property = false:suggestion
dotnet_style_qualification_for_method = false:suggestion
dotnet_style_qualification_for_event = false:suggestion
```

#### <a name="language_keywords"></a>Sprachschlüsselwörter anstelle von Framework-Typnamen für Typverweise

Diese Formatregel kann auf lokale Variablen, Methodenparameter und Klassenmember oder als separate Regel für Typmemberzugriffsausdrücke angewendet werden. Wenn der Wert auf **TRUE** festgelegt ist, wird bei Typen, die durch ein Schlüsselwort dargestellt werden, das Sprachschlüsselwort (z.B. `int` oder `Integer`) vor dem Typnamen (z.B. `Int32`) bevorzugt. Wenn der Wert **FALSE** festgelegt ist, wird der Typname vor dem Sprachschlüsselwort bevorzugt.

Die folgende Tabelle zeigt die Regelnamen, Regel-IDs, gültigen Programmiersprachen und Standardwerte:

| Regelname | Regel-ID | Anzuwendende Sprachen | Visual Studio-Standard |
| --------- | ------- | -------------------- | ----------------------|
| dotnet_style_predefined_type_for_locals_parameters_members | IDE0012 und IDE0014 | C# und Visual Basic | true:silent |
| dotnet_style_predefined_type_for_member_access | IDE0013 und IDE0015 | C# und Visual Basic | true:silent |

**dotnet\_style\_predefined\_type\_for\_locals\_parameters_members**

- Wenn diese Regel auf **TRUE** festgelegt ist, wird bei Typen, die durch ein Schlüsselwort dargestellt werden, das Sprachschlüsselwort für lokale Variablen, Methodenparameter und Klassenmember vor dem Typnamen bevorzugt.
- Wenn diese Regel auf **FALSE** festgelegt ist, wird der Typname für lokale Variablen, Methodenparameter und Klassenmember vor dem Sprachschlüsselwort bevorzugt.

Codebeispiele:

```csharp
// dotnet_style_predefined_type_for_locals_parameters_members = true
private int _member;

// dotnet_style_predefined_type_for_locals_parameters_members = false
private Int32 _member;
```

```vb
' dotnet_style_predefined_type_for_locals_parameters_members = true
Private _member As Integer

' dotnet_style_predefined_type_for_locals_parameters_members = false
Private _member As Int32
```

**dotnet\_style\_predefined\_type\_for\_member_access**

- Wenn diese Regel auf **TRUE** festgelegt ist, wird bei Typen, die durch ein Schlüsselwort dargestellt werden, das Sprachschlüsselwort für Memberzugriffsausdrücke vor dem Typnamen bevorzugt.
- Wenn diese Regel auf **FALSE** festgelegt ist, wird der Typname für Memberzugriffsausdrücke vor dem Sprachschlüsselwort bevorzugt.

Codebeispiele:

```csharp
// dotnet_style_predefined_type_for_member_access = true
var local = int.MaxValue;

// dotnet_style_predefined_type_for_member_access = false
var local = Int32.MaxValue;
```

```vb
' dotnet_style_predefined_type_for_member_access = true
Dim local = Integer.MaxValue

' dotnet_style_predefined_type_for_member_access = false
Dim local = Int32.MaxValue
```

Diese Regeln werden in einer *EDITORCONFIG-Datei* z.B. folgendermaßen angezeigt:

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
dotnet_style_predefined_type_for_member_access = true:suggestion
```

#### <a name="normalize_modifiers"></a>Einstellungen von Modifizierern

Die Formatregeln in diesem Abschnitt beziehen sich auf die Einstellungen von Modifizierern, einschließlich des Erforderns von Zugriffsmodifizierern und schreibgeschützten Modifizierern und des Angebens der gewünschten Sortierreihenfolge für Modifizierer.

In der folgenden Tabelle werden die Regelnamen, Regel-IDs, anzuwendende Programmiersprachen, Standardwerte und die erste unterstützte Version von Visual Studio angezeigt:

| Regelname | Regel-ID | Anzuwendende Sprachen | Visual Studio-Standard | Visual Studio 2017 |
| --------- | ------- | -------------------- | ----------------------| ---------------- |
| dotnet_style_require_accessibility_modifiers | IDE0040 | C# und Visual Basic | for_non_interface_members:silent | 15.5 |
| csharp_preferred_modifier_order | IDE0036 | C# | public, private, protected, internal, static, extern, new, virtual, abstract, sealed, override, readonly, unsafe, volatile, async:silent | 15.5 |
| visual_basic_preferred_modifier_order | IDE0036 | Visual Basic | Partial, Default, Private, Protected, Public, Friend, NotOverridable, Overridable, MustOverride, Overloads, Overrides, MustInherit, NotInheritable, Static, Shared, Shadows, ReadOnly, WriteOnly, Dim, Const, WithEvents, Widening, Narrowing, Custom, Async:silent | 15.5 |
| dotnet_style_readonly_field | IDE0044 | C# und Visual Basic | true:suggestion | 15.7 |

**dotnet\_style\_require\_accessibility_modifiers**

Diese Regel akzeptiert einen Wert aus der folgenden Tabelle:

| Wert | Beschreibung |
| ----- |:----------- |
| always | Es wird bevorzugt, dass Zugriffsmodifizierer angegeben werden |
| for\_non\_interface_members | Es wird bevorzugt, dass Zugriffsmodifizierer deklariert werden (außer für Members von öffentlichen Schnittstellen). (Dies entspricht **always** und fungiert als zukünftige Korrekturhilfe, falls Standard-Schnittstellenmethoden in C# hinzugefügt werden.) |
| never | Es wird bevorzugt, dass Zugriffsmodifizierer nicht angegeben werden |
| omit_if_default | Bevorzugen Sie die Angabe von Zugriffsmodifizierern, außer wenn es sich um den Standardmodifizierer handelt. |

Codebeispiele:

```csharp
// dotnet_style_require_accessibility_modifiers = always
// dotnet_style_require_accessibility_modifiers = for_non_interface_members
class MyClass
{
    private const string thisFieldIsConst = "constant";
}

// dotnet_style_require_accessibility_modifiers = never
class MyClass
{
    const string thisFieldIsConst = "constant";
}
```

**csharp_preferred_modifier_order**

- Wenn diese Regel auf eine Liste von Modifizierern festgelegt ist, wird die angegebene Sortierung bevorzugt.
- Wenn diese Regel in der Datei nicht vorhanden ist, wird keine Reihenfolge der Modifizierer bevorzugt.

Codebeispiele:

```csharp
// csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async
class MyClass
{
    private static readonly int _daysInYear = 365;
}
```

**visual_basic_preferred_modifier_order**

- Wenn diese Regel auf eine Liste von Modifizierern festgelegt ist, wird die angegebene Sortierung bevorzugt.
- Wenn diese Regel in der Datei nicht vorhanden ist, wird keine Reihenfolge der Modifizierer bevorzugt.

Codebeispiele:

```vb
' visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async
Public Class MyClass
    Private Shared ReadOnly daysInYear As Int = 365
End Class
```

**dotnet_style_readonly_field**

- Wenn diese Regel auf **TRUE** festgelegt ist, sollten Felder bevorzugt mit `readonly` (C#) oder `ReadOnly` (Visual Basic) markiert werden, wenn sie nur einmal inline oder innerhalb eines Konstruktors zugewiesen wurden.
- Wenn diese Regel auf **FALSE** festgelegt ist, müssen Sie keine Präferenz angeben, ob Felder mit `readonly` (C#) oder `ReadOnly` (Visual Basic) markiert werden.

Codebeispiele:

```csharp
// dotnet_style_readonly_field = true
class MyClass
{
    private readonly int _daysInYear = 365;
}
```

```vb
' dotnet_style_readonly_field = true
Public Class MyClass
    Private ReadOnly daysInYear As Int = 365
End Class
```

Diese Regeln werden in einer *EDITORCONFIG-Datei* z.B. folgendermaßen angezeigt:

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_require_accessibility_modifiers = always:suggestion
dotnet_style_readonly_field = true:warning

# CSharp code style settings:
[*.cs]
csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async:suggestion

# Visual Basic code style settings:
[*.vb]
visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async:suggestion
```

#### <a name="parentheses"></a>Einstellungen für Klammern

Die Stilregeln in diesem Abschnitt betreffen Einstellungen für Klammern, einschließlich der Verwendung von Klammern für arithmetische, relationale und anderen binäre Operatoren.

In der folgenden Tabelle werden die Regelnamen, Regel-IDs, anzuwendende Programmiersprachen, Standardwerte und die erste unterstützte Version von Visual Studio angezeigt:

| Regelname | Regel-ID | Anzuwendende Sprachen | Visual Studio-Standard | Visual Studio 2017 |
| --------- | ------- | -------------------- | ----------------------| ---- |
| dotnet_style_parentheses_in_arithmetic_binary_operators | IDE0047 | C# und Visual Basic | always_for_clarity:silent | 15.8 |
| dotnet_style_parentheses_in_relational_binary_operators | IDE0047 | C# und Visual Basic | always_for_clarity:silent | 15.8 |
| dotnet_style_parentheses_in_other_binary_operators | IDE0047 | C# und Visual Basic | always_for_clarity:silent | 15.8 |
| dotnet_style_parentheses_in_other_operators | IDE0047 | C# und Visual Basic | never_if_unnecessary:silent | 15.8 |

**dotnet\_style\_parentheses\_in\_arithmetic\_binary_operators**

- Ist diese Regel auf **always_for_clarity** festgelegt, sollten Klammern den Vorrang von arithmetischen Operatoren (`*`, `/`, `%`, `+`, `-`, `<<`, `>>`, `&`, `^`, `|`) verdeutlichen.
- Ist diese Regel auf **never_if_unnecessary** festgelegt, sollten keine Klammern verwendet werden, wenn der Vorrang von arithmetischen Operatoren (`*`, `/`, `%`, `+`, `-`, `<<`, `>>`, `&`, `^`, `|`) offensichtlich ist.

Codebeispiele:

```csharp
// dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity
var v = a + (b * c);

// dotnet_style_parentheses_in_arithmetic_binary_operators = never_if_unnecessary
var v = a + b * c;
```

```vb
' dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity
Dim v = a + (b * c)

' dotnet_style_parentheses_in_arithmetic_binary_operators = never_if_unnecessary
Dim v = a + b * c
```

**dotnet\_style\_parentheses\_in\_relational\_binary_operators**

- Ist diese Regel auf **always_for_clarity** festgelegt, sollten Klammern den Vorrang von relationalen Operatoren (`>`, `<`, `<=`, `>=`, `is`, `as`, `==`, `!=`) verdeutlichen.
- Ist diese Regel auf **never_if_unnecessary** festgelegt, sollten keine Klammern verwendet werden, wenn der Vorrang von relationalen Operatoren (`>`, `<`, `<=`, `>=`, `is`, `as`, `==`, `!=`) offensichtlich ist.

Codebeispiele:

```csharp
// dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity
var v = (a < b) == (c > d);

// dotnet_style_parentheses_in_relational_binary_operators = never_if_unnecessary
var v = a < b == c > d;
```

```vb
' dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity
Dim v = (a < b) = (c > d)

' dotnet_style_parentheses_in_relational_binary_operators = never_if_unnecessary
Dim v = a < b = c > d
```

**dotnet\_style\_parentheses\_in\_other\_binary_operators**

- Ist diese Regel auf **always_for_clarity** festgelegt, sollten Klammern den Vorrang von anderen binären Operatoren (`&&`, `||`, `??`) verdeutlichen.
- Ist diese Regel auf **never_if_unnecessary** festgelegt, sollten keine Klammern verwendet werden, wenn der Vorrang von anderen binären Operatoren (`&&`, `||`, `??`) offensichtlich ist.

Codebeispiele:

```csharp
// dotnet_style_parentheses_in_other_binary_operators = always_for_clarity
var v = a || (b && c);

// dotnet_style_parentheses_in_other_binary_operators = never_if_unnecessary
var v = a || b && c;
```

```vb
' dotnet_style_parentheses_in_other_binary_operators = always_for_clarity
Dim v = a OrElse (b AndAlso c)

' dotnet_style_parentheses_in_other_binary_operators = never_if_unnecessary
Dim v = a OrElse b AndAlso c
```

**dotnet\_style\_parentheses\_in\_other_operators**

- Ist diese Regel auf **always_for_clarity** festgelegt, sollten Klammern den Vorrang von Operatoren verdeutlichen.
- Ist diese Regel auf **never_if_unnecessary** festgelegt, sollten keine Klammern verwendet werden, wenn der Vorrang von Operatoren offensichtlich ist.

Codebeispiele:

```csharp
// dotnet_style_parentheses_in_other_operators = always_for_clarity
var v = (a.b).Length;

// dotnet_style_parentheses_in_other_operators = never_if_unnecessary
var v = a.b.Length;
```

```vb
' dotnet_style_parentheses_in_other_operators = always_for_clarity
Dim v = (a.b).Length

' dotnet_style_parentheses_in_other_operators = never_if_unnecessary
Dim v = a.b.Length
```

Diese Regeln werden in einer *EDITORCONFIG-Datei* z.B. folgendermaßen angezeigt:

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_operators = never_if_unnecessary:silent
```

#### <a name="expression_level"></a>Einstellungen auf Ausdrucksebene

Die Formatierungsregeln in diesem Abschnitt betreffen Einstellungen auf Ausdrucksebene, einschließlich der Verwendung von Objektinitialisierern, Auflistungsinitialisierern, expliziter oder abgeleiteter Tupelnamen und abgeleiteter anonymer Typen.

In der folgenden Tabelle werden die Regelnamen, Regel-IDs, anzuwendende Programmiersprachen, Standardwerte und die erste unterstützte Version von Visual Studio angezeigt:

| Regelname | Regel-ID | Anzuwendende Sprachen | Visual Studio-Standard | Visual Studio 2017 |
| --------- | ------- | -------------------- | ----------------------| ---- |
| dotnet_style_object_initializer | IDE0017 | C# und Visual Basic | true:suggestion | Erste Version |
| dotnet_style_collection_initializer | IDE0028 | C# und Visual Basic | true:suggestion | Erste Version |
| dotnet_style_explicit_tuple_names | IDE0033 | C# 7.0 und höher und Visual Basic 15 und höher | true:suggestion | Erste Version |
| dotnet_style_prefer_inferred_tuple_names | IDE0037 | C# 7.1 und höher und Visual Basic 15 und höher | true:suggestion | 15,6 |
| dotnet_style_prefer_inferred_anonymous_type_member_names | IDE0037 | C# und Visual Basic | true:suggestion | 15,6 |
| dotnet_style_prefer_auto_properties | IDE0032 | C# und Visual Basic | true:silent | 15.7 |
| dotnet_style_prefer_is_null_check_over_reference_equality_method | IDE0041 | C# und Visual Basic | true:suggestion | 15.7 |
| dotnet_style_prefer_conditional_expression_over_assignment | IDE0045 | C# und Visual Basic | true:silent | 15.8 |
| dotnet_style_prefer_conditional_expression_over_return | IDE0046 | C# und Visual Basic | true:silent | 15.8 |

**dotnet\_style\_object_initializer**

- Wenn diese Regel auf **TRUE** festgelegt ist, wird, sofern möglich, die Initialisierung von Objekten mithilfe von Objektinitialisierern bevorzugt.
- Wenn diese Regel auf **FALSE** festgelegt ist, wird die Initialisierung von Objekten mithilfe von Objektinitialisierern *nicht* bevorzugt.

Codebeispiele:

```csharp
// dotnet_style_object_initializer = true
var c = new Customer() { Age = 21 };

// dotnet_style_object_initializer = false
var c = new Customer();
c.Age = 21;
```

```vb
' dotnet_style_object_initializer = true
Dim c = New Customer() With {.Age = 21}

' dotnet_style_object_initializer = false
Dim c = New Customer()
c.Age = 21
```

**dotnet\_style\_collection_initializer**

- Wenn diese Regel auf **TRUE** festgelegt ist, wird, sofern möglich, die Initialisierung von Auflistungen mithilfe von Auflistungsinitialisierern bevorzugt.
- Wenn diese Regel auf **FALSE** festgelegt ist, wird die Initialisierung von Auflistungen mithilfe von Auflistungsinitialisierern *nicht* bevorzugt.

Codebeispiele:

```csharp
// dotnet_style_collection_initializer = true
var list = new List<int> { 1, 2, 3 };

// dotnet_style_collection_initializer = false
var list = new List<int>();
list.Add(1);
list.Add(2);
list.Add(3);
```

```vb
' dotnet_style_collection_initializer = true
Dim list = New List(Of Integer) From {1, 2, 3}

' dotnet_style_collection_initializer = false
Dim list = New List(Of Integer)
list.Add(1)
list.Add(2)
list.Add(3)
```

**dotnet\_style\_explicit\_tuple_names**

- Wenn diese Regel auf **TRUE** festgelegt ist, werden Tupelnamen vor ItemX-Eigenschaften bevorzugt.
- Wenn diese Regel auf **FALSE** festgelegt ist, werden ItemX-Eigenschaften vor Tupelnamen bevorzugt.

Codebeispiele:

```csharp
// dotnet_style_explicit_tuple_names = true
(string name, int age) customer = GetCustomer();
var name = customer.name;

// dotnet_style_explicit_tuple_names = false
(string name, int age) customer = GetCustomer();
var name = customer.Item1;
```

```vb
 ' dotnet_style_explicit_tuple_names = true
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.name

' dotnet_style_explicit_tuple_names = false
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.Item1
```

**dotnet\_style\_prefer\_inferred\_tuple_names**

- Wenn diese Regel auf **TRUE** festgelegt ist, werden abgeleitete Tupelelementnamen bevorzugt.
- Wenn diese Regel auf **FALSE** festgelegt ist, werden explizite Tupelelementnamen bevorzugt.

Codebeispiele:

```csharp
// dotnet_style_prefer_inferred_tuple_names = true
var tuple = (age, name);

// dotnet_style_prefer_inferred_tuple_names = false
var tuple = (age: age, name: name);
```

```vb
' dotnet_style_prefer_inferred_tuple_names = true
Dim tuple = (name, age)

' dotnet_style_prefer_inferred_tuple_names = false
Dim tuple = (name:=name, age:=age)
```

**dotnet\_style\_prefer\_inferred\_anonymous\_type\_member_names**

- Wenn diese Regel auf **TRUE** festgelegt ist, werden abgeleitete Membernamen vom anonymen Typ bevorzugt.
- Wenn diese Regel auf **FALSE** festgelegt ist, werden explizite Membernamen vom anonymen Typ bevorzugt.

Codebeispiele:

```csharp
// dotnet_style_prefer_inferred_anonymous_type_member_names = true
var anon = new { age, name };

// dotnet_style_prefer_inferred_anonymous_type_member_names = false
var anon = new { age = age, name = name };
```

```vb
' dotnet_style_prefer_inferred_anonymous_type_member_names = true
Dim anon = New With {name, age}

' dotnet_style_prefer_inferred_anonymous_type_member_names = false
Dim anon = New With {.name = name, .age = age}
```

**dotnet\_style\_prefer\_auto\_properties**

- Wenn diese Regel auf **TRUE** festgelegt ist, werden automatische Eigenschaften gegenüber Eigenschaften mit privaten Unterstützungsfeldern bevorzugt.
- Wenn diese Regel auf **FALSE** festgelegt ist, werden Eigenschaften mit privaten Unterstützungsfeldern gegenüber automatischen Eigenschaften bevorzugt.

Codebeispiele:

```csharp
// dotnet_style_prefer_auto_properties = true
private int Age { get; }

// dotnet_style_prefer_auto_properties = false
private int age;

public int Age
{
    get
    {
        return age;
    }
}
```

```vb
' dotnet_style_prefer_auto_properties = true
Public ReadOnly Property Age As Integer

' dotnet_style_prefer_auto_properties = false
Private _age As Integer

Public ReadOnly Property Age As Integer
    Get
        return _age
    End Get
End Property
```

**dotnet\_style\_prefer\_is\_null\_check\_over\_reference\_equality\_method**

- Wenn diese Regel auf **TRUE** festgelegt ist, wird die Verwendung einer NULL-Überprüfung mit Musterabgleich gegenüber object.ReferenceEquals bevorzugt.
- Wenn diese Regel auf **FALSE** festgelegt ist, wird object.ReferenceEquals gegenüber einer NULL-Überprüfung mit Musterabgleich bevorzugt.

Codebeispiele:

```csharp
// dotnet_style_prefer_is_null_check_over_reference_equality_method = true
if (value is null)
    return;

// dotnet_style_prefer_is_null_check_over_reference_equality_method = false
if (object.ReferenceEquals(value, null))
    return;
```

```vb
' dotnet_style_prefer_is_null_check_over_reference_equality_method = true
If value Is Nothing
    Return
End If

' dotnet_style_prefer_is_null_check_over_reference_equality_method = false
If Object.ReferenceEquals(value, Nothing)
    Return
End If
```

**dotnet\_style\_prefer\_conditional\_expression\_over_assignment**

- Ist diese Regel auf **TRUE** festgelegt, sollten Sie Zuweisungen mit einem tertiären bedingten Operator einer if-else-Anweisung vorziehen.
- Ist diese Regel auf **FALSE** festgelegt, sollten Sie Zuweisungen mit einer if-else-Anweisung einem ternärer bedingter Operator vorziehen.

Codebeispiele:

```csharp
// dotnet_style_prefer_conditional_expression_over_assignment = true
string s = expr ? "hello" : "world";

// dotnet_style_prefer_conditional_expression_over_assignment = false
string s;
if (expr)
{
    s = "hello";
}
else
{
    s = "world";
}
```

```vb
' dotnet_style_prefer_conditional_expression_over_assignment = true
Dim s As String = If(expr, "hello", "world")

' dotnet_style_prefer_conditional_expression_over_assignment = false
Dim s As String
If expr Then
    s = "hello"
Else
    s = "world"
End If
```

**dotnet\_style\_prefer\_conditional\_expression\_over_return**

- Ist diese Regel auf **TRUE** festgelegt, sollten return-Anweisungen einen tertiären bedingten Operator statt einer if-else-Anweisung verwenden.
- Ist diese Regel auf **FALSE** festgelegt, sollten return-Anweisungen eine if-else-Anweisung statt einem ternären bedingten Operator verwenden.

Codebeispiele:

```csharp
// dotnet_style_prefer_conditional_expression_over_return = true
return expr ? "hello" : "world"

// dotnet_style_prefer_conditional_expression_over_return = false
if (expr)
{
    return "hello";
}
else
{
    return "world";
}
```

```vb
' dotnet_style_prefer_conditional_expression_over_return = true
Return If(expr, "hello", "world")

' dotnet_style_prefer_conditional_expression_over_return = false
If expr Then
    Return "hello"
Else
    Return "world"
End If
```

Diese Regeln werden in einer *EDITORCONFIG-Datei* z.B. folgendermaßen angezeigt:

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_object_initializer = true:suggestion
dotnet_style_collection_initializer = true:suggestion
dotnet_style_explicit_tuple_names = true:suggestion
dotnet_style_prefer_inferred_tuple_names = true:suggestion
dotnet_style_prefer_inferred_anonymous_type_member_names = true:suggestion
dotnet_style_prefer_auto_properties = true:silent
dotnet_style_prefer_conditional_expression_over_assignment = true:suggestion
dotnet_style_prefer_conditional_expression_over_return = true:suggestion
```

#### <a name="null_checking"></a>Einstellungen für die NULL-Überprüfung

Die Formatierungsregeln in diesem Abschnitt betreffen die Einstellungen der NULL-Überprüfung.

In der folgenden Tabelle werden die Regelnamen, Regel-IDs, anzuwendende Programmiersprachen, Standardwerte und die erste unterstützte Version von Visual Studio angezeigt:

| Regelname | Regel-ID | Anzuwendende Sprachen | Visual Studio-Standard | Visual Studio 2017 |
| --------- | ------- | -------------------- | ----------------------| ---- |
| dotnet_style_coalesce_expression | IDE0029 | C# und Visual Basic | true:suggestion | Erste Version |
| dotnet_style_null_propagation | IDE0031 | C# 6.0+ und Visual Basic 14+ | true:suggestion | Erste Version |

**dotnet\_style\_coalesce_expression**

- Wenn diese Regel auf **TRUE** festgelegt ist, werden NULL-Sammelausdrücke vor der ternären Operatorüberprüfung bevorzugt.
- Wenn diese Regel auf **FALSE** festgelegt ist, wird die ternäre Operatorüberprüfung vor NULL-Sammelausdrücken bevorzugt.

Codebeispiele:

```csharp
// dotnet_style_coalesce_expression = true
var v = x ?? y;

// dotnet_style_coalesce_expression = false
var v = x != null ? x : y; // or
var v = x == null ? y : x;
```

```vb
' dotnet_style_coalesce_expression = true
Dim v = If(x, y)

' dotnet_style_coalesce_expression = false
Dim v = If(x Is Nothing, y, x) ' or
Dim v = If(x IsNot Nothing, x, y)
```

**dotnet\_style\_null_propagation**

- Wenn diese Regel auf **TRUE** festgelegt ist, wird, sofern möglich, der Operator mit NULL-Bedingung bevorzugt.
- Wenn diese Regel auf **FALSE** festgelegt ist, wird nach Möglichkeit die ternäre NULL-Überprüfung verwendet.

Codebeispiele:

```csharp
// dotnet_style_null_propagation = true
var v = o?.ToString();

// dotnet_style_null_propagation = false
var v = o == null ? null : o.ToString(); // or
var v = o != null ? o.String() : null;
```

```vb
' dotnet_style_null_propagation = true
Dim v = o?.ToString()

' dotnet_style_null_propagation = false
Dim v = If(o Is Nothing, Nothing, o.ToString()) ' or
Dim v = If(o IsNot Nothing, o.ToString(), Nothing)
```

Diese Regeln werden in einer *EDITORCONFIG-Datei* z.B. folgendermaßen angezeigt:

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_null_propagation = true:suggestion
```

### <a name="c-code-style-settings"></a>Einstellungen für das C#-Codeformat

Die Formatregeln in diesem Abschnitt gelten nur für C#.

#### <a name="implicit-and-explicit-types"></a>Implizite und explizite Typen

Die Formatregeln in diesem Abschnitt (Regel-IDs IDE0007 und IDE0008) betreffen die Verwendung des Schlüsselworts [var](/dotnet/csharp/language-reference/keywords/var) im Vergleich zu einem expliziten Typ in einer Variablendeklaration. Diese Regel kann getrennt auf integrierte Typen angewendet werden, wenn diese Typen offensichtlich sind und sich an einer anderen Position befinden.

Die folgende Tabelle zeigt die Regelnamen, gültigen Programmiersprachen und Standardwerte:

| Regelname | Anzuwendende Sprachen | Visual Studio-Standard |
| ----------- | -------------------- | ----------------------|
| csharp_style_var_for_built_in_types | C# | true:silent |
| csharp_style_var_when_type_is_apparent | C# | true:silent |
| csharp_style_var_elsewhere | C# | true:silent |

**csharp\_style\_var\_for\_built\_in_types**

- Wenn diese Regel auf **TRUE** festgelegt ist, wird bevorzugt `var` zum Deklarieren von Variablen mit integrierten Systemtypen wie `int` verwendet.
- Wenn diese Regel auf **FALSE** festgelegt ist, wird der explizite Typ vor `var` zum Deklarieren von Variablen mit integrierten Systemtypen wie `int` bevorzugt.

Codebeispiele:

```csharp
// csharp_style_var_for_built_in_types = true
var x = 5;

// csharp_style_var_for_built_in_types = false
int x = 5;
```

**csharp\_style\_var\_when\_type\_is_apparent**

- Wenn diese Regel auf **TRUE** festgelegt ist, wird `var` bevorzugt, wenn der Typ bereits auf der rechten Seite eines Deklarationsausdrucks erwähnt wird.
- Wenn diese Regel auf **FALSE** festgelegt ist, wird der explizite Typ vor `var` bevorzugt, wenn der Typ bereits auf der rechten Seite eines Deklarationsausdrucks erwähnt wird.

Codebeispiele:

```csharp
// csharp_style_var_when_type_is_apparent = true
var obj = new Customer();

// csharp_style_var_when_type_is_apparent = false
Customer obj = new Customer();
```

**csharp\_style\_var_elsewhere**

- Wenn diese Regel auf **TRUE** festgelegt ist, wird `var` in allen Fällen vor dem expliziten Typ bevorzugt, es sei denn, es wird von einer anderen Codeformatregel überschrieben.
- Wenn diese Regel auf **FALSE** festgelegt ist, wird der explizite Typ in allen Fällen vor `var` bevorzugt, es sei denn, er wird von einer anderen Codeformatregel überschrieben.

Codebeispiele:

```csharp
// csharp_style_var_elsewhere = true
var f = this.Init();

// csharp_style_var_elsewhere = false
bool f = this.Init();
```

*EDITORCONFIG-Beispieldatei:*

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_var_for_built_in_types = true:suggestion
csharp_style_var_when_type_is_apparent = true:suggestion
csharp_style_var_elsewhere = true:suggestion
```

#### <a name="expression_bodied_members"></a>Ausdruckskörpermember

Die Formatregeln in diesem Abschnitt betreffen die Verwendung von [Ausdruckskörpermember](/dotnet/csharp/programming-guide/statements-expressions-operators/expression-bodied-members), wenn die Logik aus einem einzelnen Ausdruck besteht. Diese Regel kann auf Methoden, Konstruktoren, Operatoren, Eigenschaften, Indexer und Accessoren angewendet werden.

In der folgenden Tabelle werden die Regelnamen, Regel-IDs, anzuwendende Sprachversionen, Standardwerte und die erste unterstützte Version von Visual Studio angezeigt:

| Regelname | Regel-ID | Anzuwendende Sprachen | Visual Studio-Standard | Visual Studio 2017 |
| --------- | ------- | -------------------- | ----------------------| ---------------- |
| csharp_style_expression_bodied_methods | IDE0022 | C# 6.0 und höher | false:silent | 15.3 |
| csharp_style_expression_bodied_constructors | IDE0021 | C# 7.0 und höher | false:silent | 15.3 |
| csharp_style_expression_bodied_operators | IDE0023 und IDE0024 | C# 7.0 und höher | false:silent | 15.3 |
| csharp_style_expression_bodied_properties | IDE0025 | C# 7.0 und höher | true:silent | 15.3 |
| csharp_style_expression_bodied_indexers | IDE0026 | C# 7.0 und höher | true:silent | 15.3 |
| csharp_style_expression_bodied_accessors | IDE0027 | C# 7.0 und höher | true:silent | 15.3 |

**csharp\_style\_expression\_bodied_methods**

Diese Regel akzeptiert Werte aus der folgenden Tabelle:

| Wert | Beschreibung |
| ----- |:----------- |
| true | Ausdruckskörpermember werden für Methoden bevorzugt |
| when_on_single_line | Ausdruckskörpermember werden für Methoden bevorzugt, wenn diese aus einer einzelnen Zeile bestehen |
| False | Blocktexte werden für Methoden bevorzugt |

Codebeispiele:

```csharp
// csharp_style_expression_bodied_methods = true
public int GetAge() => this.Age;

// csharp_style_expression_bodied_methods = false
public int GetAge() { return this.Age; }
```

**csharp\_style\_expression\_bodied_constructors**

Diese Regel akzeptiert Werte aus der folgenden Tabelle:

| Wert | Beschreibung |
| ----- |:----------- |
| true | Ausdruckskörpermember werden für Konstruktoren bevorzugt |
| when_on_single_line | Ausdruckskörpermember werden für Konstruktoren bevorzugt, wenn diese aus einer einzelnen Zeile bestehen |
| False | Blocktexte werden für Konstruktoren bevorzugt |

Codebeispiele:

```csharp
// csharp_style_expression_bodied_constructors = true
public Customer(int age) => Age = age;

// csharp_style_expression_bodied_constructors = false
public Customer(int age) { Age = age; }
```

**csharp\_style\_expression\_bodied_operators**

Diese Regel akzeptiert Werte aus der folgenden Tabelle:

| Wert | Beschreibung |
| ----- |:----------- |
| true | Ausdruckskörpermember werden für Operatoren bevorzugt |
| when_on_single_line | Ausdruckskörpermember werden für Operatoren bevorzugt, wenn diese aus einer einzelnen Zeile bestehen |
| False | Blocktexte werden für Operatoren bevorzugt |

Codebeispiele:

```csharp
// csharp_style_expression_bodied_operators = true
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
    => new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary);

// csharp_style_expression_bodied_operators = false
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
{ return new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary); }
```

**csharp\_style\_expression\_bodied_properties**

Diese Regel akzeptiert Werte aus der folgenden Tabelle:

| Wert | Beschreibung |
| ----- |:----------- |
| true | Ausdruckskörpermember werden für Eigenschaften bevorzugt |
| when_on_single_line | Ausdruckskörpermember werden für Eigenschaften bevorzugt, wenn diese aus einer einzelnen Zeile bestehen |
| False | Blocktexte werden für Eigenschaften bevorzugt |

Codebeispiele:

```csharp
// csharp_style_expression_bodied_properties = true
public int Age => _age;

// csharp_style_expression_bodied_properties = false
public int Age { get { return _age; }}
```

**csharp\_style\_expression\_bodied_indexers**

Diese Regel akzeptiert Werte aus der folgenden Tabelle:

| Wert | Beschreibung |
| ----- |:----------- |
| true | Ausdruckskörpermember werden für Indexer bevorzugt |
| when_on_single_line | Ausdruckskörpermember werden für Indexer bevorzugt, wenn diese aus einer einzelnen Zeile bestehen |
| False | Blocktexte werden für Indexer bevorzugt |

Codebeispiele:

```csharp
// csharp_style_expression_bodied_indexers = true
public T this[int i] => _values[i];

// csharp_style_expression_bodied_indexers = false
public T this[int i] { get { return _values[i]; } }
```

**csharp\_style\_expression\_bodied_accessors**

Diese Regel akzeptiert Werte aus der folgenden Tabelle:

| Wert | Beschreibung |
| ----- |:----------- |
| true | Ausdruckskörpermember werden für Accessoren bevorzugt |
| when_on_single_line | Ausdruckskörpermember werden für Accessoren bevorzugt, wenn diese aus einer einzelnen Zeile bestehen |
| False | Blocktexte werden für Accessoren bevorzugt |

Codebeispiele:

```csharp
// csharp_style_expression_bodied_accessors = true
public int Age { get => _age; set => _age = value; }

// csharp_style_expression_bodied_accessors = false
public int Age { get { return _age; } set { _age = value; } }
```

*EDITORCONFIG-Beispieldatei:*

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_methods = false:silent
csharp_style_expression_bodied_constructors = false:silent
csharp_style_expression_bodied_operators = false:silent
csharp_style_expression_bodied_properties = true:suggestion
csharp_style_expression_bodied_indexers = true:suggestion
csharp_style_expression_bodied_accessors = true:suggestion
```

#### <a name="pattern_matching"></a>Musterabgleich

Die Formatregeln in diesem Abschnitt betreffen die Verwendung von [Mustervergleich](/dotnet/csharp/pattern-matching) in C#.

Die folgende Tabelle zeigt die Regelnamen, Regel-IDs, gültigen Sprachversionen und Standardwerte:

| Regelname | Regel-ID | Anzuwendende Sprachen | Visual Studio-Standard |
| --------- | ------- | -------------------- | ----------------------|
| csharp_style_pattern_matching_over_is_with_cast_check | IDE0020 | C# 7.0 und höher | true:suggestion |
| csharp_style_pattern_matching_over_as_with_null_check | IDE0019 | C# 7.0 und höher | true:suggestion |

**csharp\_style\_pattern\_matching\_over\_is\_with\_cast_check**

- Wenn diese Regel auf **TRUE** festgelegt ist, wird der Mustervergleich vor `is`-Ausdrücken mit Typumwandlungen bevorzugt.
- Wenn diese Regel auf **FALSE** festgelegt ist, werden `is`-Ausdrücke mit Typumwandlungen vor dem Mustervergleich bevorzugt.

Codebeispiele:

```csharp
// csharp_style_pattern_matching_over_is_with_cast_check = true
if (o is int i) {...}

// csharp_style_pattern_matching_over_is_with_cast_check = false
if (o is int) {var i = (int)o; ... }
```

**csharp\_style\_pattern\_matching\_over\_as\_with\_null_check**

- Wenn diese Regel auf **TRUE** festgelegt ist, wird der Mustervergleich vor `as`-Ausdrücken mit NULL-Überprüfungen für die Bestimmung bevorzugt, ob etwas von einem bestimmten Typ ist.
- Wenn diese Regel auf **FALSE** festgelegt ist, werden `as`-Ausdrücke mit NULL-Überprüfungen vor dem Mustervergleich für die Bestimmung bevorzugt, ob etwas von einem bestimmten Typ ist.

Codebeispiele:

```csharp
// csharp_style_pattern_matching_over_as_with_null_check = true
if (o is string s) {...}

// csharp_style_pattern_matching_over_as_with_null_check = false
var s = o as string;
if (s != null) {...}
```

*EDITORCONFIG-Beispieldatei:*

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
```

#### <a name="inlined_variable_declarations"></a>Inline-Variablendeklarationen

Diese Formatregel bezieht sich darauf, ob `out`-Variablen inline deklariert werden oder nicht. Ab C# 7 können Sie [in der Argumentliste eines Methodenaufrufs eine out-Variable deklarieren](/dotnet/csharp/language-reference/keywords/out-parameter-modifier#calling-a-method-with-an-out-argument), anstatt dies in einer separaten Variablendeklaration zu machen.

Die folgende Tabelle zeigt die Regelnamen, Regel-IDs, gültigen Sprachversionen und Standardwerte:

| Regelname | Regel-ID | Anzuwendende Sprachen | Visual Studio-Standard |
| --------- | -------- | -------------------- | ----------------------|
| csharp_style_inlined_variable_declaration | IDE0018 | C# 7.0 und höher | true:suggestion |

**csharp\_style\_inlined\_variable_declaration**

- Wenn diese Regel auf **TRUE** festgelegt ist, werden, sofern möglich, die `out`-Variablen bevorzugt, die in der Argumentliste eines Methodenaufrufs inline deklariert werden.
- Wenn diese Regel auf **FALSE** festgelegt ist, werden zu deklarierende `out`-Variablen vor dem Methodenaufruf bevorzugt.

Codebeispiele:

```csharp
// csharp_style_inlined_variable_declaration = true
if (int.TryParse(value, out int i) {...}

// csharp_style_inlined_variable_declaration = false
int i;
if (int.TryParse(value, out i) {...}
```

*EDITORCONFIG-Beispieldatei:*

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```

#### <a name="expression_level_csharp"></a>Einstellungen auf Ausdrucksebene

Die Stilregeln in diesem Abschnitt beziehen sich auf die Einstellungen auf Ausdrucksebene, einschließlich der Verwendung von [default-Ausdrücken](/dotnet/csharp/programming-guide/statements-expressions-operators/default-value-expressions#default-literal-and-type-inference), dekonstruierten Variablen und lokalen Funktionen statt anonymen Funktionen.

In der folgenden Tabelle werden der Regelname, Regel-IDs, anzuwendende Sprachversionen, Standardwerte und die erste unterstützte Version von Visual Studio angezeigt:

| Regelname | Regel-ID | Anzuwendende Sprachen | Visual Studio-Standard | Visual Studio 2017 |
| --------- | ------- | -------------------- | ----------------------| ---------------- |
| csharp_prefer_simple_default_expression | IDE0034 | C# 7.1+ | true:suggestion | 15.3 |
| csharp_style_deconstructed_variable_declaration | IDE0042 | C# 7.0 und höher | true:suggestion | 15.5 |
| csharp_style_pattern_local_over_anonymous_function | IDE0039 | C# 7.0 und höher | true:suggestion | 15.5 |

**csharp\_prefer\_simple\_default_expression**

Diese Formatregel bezieht sich auf die Verwendung des [`default`-Literals für Standardwertausdrücke](/dotnet/csharp/programming-guide/statements-expressions-operators/default-value-expressions#default-literal-and-type-inference), wenn der Compiler den Typ des Ausdrucks ableiten kann.

- Wenn diese Regel auf **TRUE** festgelegt ist, wird `default` vor `default(T)` bevorzugt.
- Wenn diese Regel auf **FALSE** festgelegt ist, wird `default(T)` vor `default` bevorzugt.

Codebeispiele:

```csharp
// csharp_prefer_simple_default_expression = true
void DoWork(CancellationToken cancellationToken = default) { ... }

// csharp_prefer_simple_default_expression = false
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }
```

**csharp\_style\_deconstructed\_variable_declaration**

- Wenn diese Regel auf **TRUE** festgelegt ist, wird die Deklaration von dekonstruierten Variablen bevorzugt.
- Wenn diese Regel auf **FALSE** festgelegt ist, wird die Deklaration von dekonstruierten Variablen nicht bevorzugt.

Codebeispiele:

```csharp
// csharp_style_deconstructed_variable_declaration = true
var (name, age) = GetPersonTuple();
Console.WriteLine($"{name} {age}");

(int x, int y) = GetPointTuple();
Console.WriteLine($"{x} {y}");

// csharp_style_deconstructed_variable_declaration = false
var person = GetPersonTuple();
Console.WriteLine($"{person.name} {person.age}");

(int x, int y) point = GetPointTuple();
Console.WriteLine($"{point.x} {point.y}");
```

**csharp\_style\_pattern\_local\_over\_anonymous_function**

- Wenn diese Regel auf **TRUE** festgelegt ist, werden lokale Funktionen vor anonymen Funktionen bevorzugt.
- Wenn diese Regel auf **FALSE** festgelegt ist, werden anonyme Funktionen gegenüber lokalen Funktionen bevorzugt.

Codebeispiele:

```csharp
// csharp_style_pattern_local_over_anonymous_function = true
int fibonacci(int n)
{
    return n <= 1 ? 1 : fibonacci(n-1) + fibonacci(n-2);
}

// csharp_style_pattern_local_over_anonymous_function = false
Func<int, int> fibonacci = null;
fibonacci = (int n) =>
{
    return n <= 1 ? 1 : fibonacci(n - 1) + fibonacci(n - 2);
};
```

*EDITORCONFIG-Beispieldatei:*

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_prefer_simple_default_expression = true:suggestion
csharp_style_deconstructed_variable_declaration = true:suggestion
csharp_style_pattern_local_over_anonymous_function = true:suggestion
```

#### <a name="null_checking_csharp"></a>Einstellungen für die NULL-Überprüfung

Diese Formatregeln beziehen sich auf die Syntax hinsichtlich der `null`-Prüfung, einschließlich der Verwendung von `throw`-Ausdrücken oder `throw`-Anweisungen; ferner bezieht sie sich darauf, ob eine NULL-Überprüfung durchgeführt oder der bedingte Sammeloperator (`?.`) verwendet werden soll, wenn ein [Lambdaausdruck](/dotnet/csharp/lambda-expressions) aufgerufen wird.

Die folgende Tabelle zeigt die Regelnamen, Regel-IDs, gültigen Sprachversionen und Standardwerte:

| Regelname | Regel-ID | Anzuwendende Sprachen | Visual Studio-Standard |
| --------- | ------- | -------------------- | ----------------------|
| csharp_style_throw_expression | IDE0016 | C# 7.0 und höher | true:suggestion |
| csharp_style_conditional_delegate_call | IDE0041 | C# 6.0 und höher | true:suggestion |

**csharp\_style\_throw_expression**

- Wenn diese Regel auf **TRUE** festgelegt ist, wird die Verwendung von `throw`-Ausdrücken vor `throw`-Anweisungen bevorzugt.
- Wenn diese Regel auf **FALSE** festgelegt ist, wird die Verwendung von `throw`-Anweisungen vor `throw`-Ausdrücken bevorzugt.

Codebeispiele:

```csharp
// csharp_style_throw_expression = true
this.s = s ?? throw new ArgumentNullException(nameof(s));

// csharp_style_throw_expression = false
if (s == null) { throw new ArgumentNullException(nameof(s)); }
this.s = s;
```

**csharp\_style\_conditional\_delegate_call**

- Wenn diese Regel auf **TRUE** festgelegt ist, wird beim Abrufen eines Lambdaausdrucks die Verwendung des bedingten Sammeloperators (`?.`) vor der Durchführung einer NULL-Überprüfung bevorzugt.
- Wenn diese Regel auf **FALSE** festgelegt ist, wird vor dem Abrufen eines Lambdaausdrucks die Durchführung einer NULL-Überprüfung vor der Verwendung des bedingten Sammeloperators (`?.`) bevorzugt.

Codebeispiele:

```csharp
// csharp_style_conditional_delegate_call = true
func?.Invoke(args);

// csharp_style_conditional_delegate_call = false
if (func != null) { func(args); }
```

*EDITORCONFIG-Beispieldatei:*

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestion
csharp_style_conditional_delegate_call = false:suggestion
```

#### <a name="code_block"></a>Codeblockeinstellungen

Diese Formatregel bezieht sich auf die Verwendung der geschweiften Klammern `{ }`, die Codeblöcke umgeben.

In der folgenden Tabelle werden der Regelname, Regel-IDs, anzuwendende Sprachversionen, Standardwerte und die erste unterstützte Version von Visual Studio angezeigt:

| Regelname | Regel-ID | Anzuwendende Sprachen | Visual Studio-Standard | Visual Studio 2017 |
| --------- | ------- | -------------------- | ----------------------| ---------------- |
| csharp_prefer_braces | IDE0011 | C# | true:silent | 15.3 |

**csharp\_prefer\_braces**

- Wenn diese Regel auf **TRUE** festgelegt ist, werden geschweifte Klammern bevorzugt, auch für eine Codezeile.
- Wenn diese Regel auf **FALSE** festgelegt ist, werden, sofern zulässig, keine geschweiften Klammern bevorzugt.

Codebeispiele:

```csharp
// csharp_prefer_braces = true
if (test) { this.Display(); }

// csharp_prefer_braces = false
if (test) this.Display();
```

*EDITORCONFIG-Beispieldatei:*

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_prefer_braces = true:silent
```

## <a name="formatting-conventions"></a>Formatierungskonventionen

Die meisten Regeln für Formatierungskonventionen weisen folgendes Format auf:

`rule_name = false|true`

Sie geben entweder **TRUE** (dieses Format bevorzugen) oder **FALSE** (dieses Format nicht bevorzugen) an. Sie geben keinen Schweregrad an. Für einige Regeln geben Sie statt „TRUE“ und „FALSE“ andere Werte an, um zu beschreiben, wann und wo die Regel angewendet wird.

In der folgenden Liste werden die Regeln für Formatierungskonventionen angezeigt, die in Visual Studio verfügbar sind:

- .NET-Formatierungseinstellungen
    - [Organisieren von Using-Direktiven](#usings)
        - dotnet_sort_system_directives_first
        - dotnet_separate_import_directive_groups
- C#-Formatierungseinstellungen
    - [Newline-Optionen](#newline)
        - csharp_new_line_before_open_brace
        - csharp_new_line_before_else
        - csharp_new_line_before_catch
        - csharp_new_line_before_finally
        - csharp_new_line_before_members_in_object_initializers
        - csharp_new_line_before_members_in_anonymous_types
        - csharp_new_line_between_query_expression_clauses
    - [Einzugsoptionen](#indent)
        - csharp_indent_case_contents
        - csharp_indent_switch_labels
        - csharp_indent_labels
    - [Abstandsoptionen](#spacing)
        - csharp_space_after_cast
        - csharp_space_after_keywords_in_control_flow_statements
        - csharp_space_between_method_declaration_parameter_list_parentheses
        - csharp_space_between_method_call_parameter_list_parentheses
        - csharp_space_between_parentheses
        - csharp_space_before_colon_in_inheritance_clause
        - csharp_space_after_colon_in_inheritance_clause
        - csharp_space_around_binary_operators
        - csharp_space_between_method_declaration_empty_parameter_list_parentheses
        - csharp_space_between_method_call_name_and_opening_parenthesis
        - csharp_space_between_method_call_empty_parameter_list_parentheses
    - [Umbruchoptionen](#wrapping)
        - csharp_preserve_single_line_statements
        - csharp_preserve_single_line_blocks

### <a name="net-formatting-settings"></a>.NET-Formatierungseinstellungen

Die Formatierungsregeln in diesem Abschnitt gelten für C# und für Visual Basic.

#### <a name="usings"></a>Organisieren von Using-Direktiven

Diese Formatierungsregel bezieht sich auf die Platzierung von System.* using-Direktiven in Bezug auf andere using-Direktiven.

In der folgenden Tabelle werden der Regelname, anzuwendende Sprachen, der Standardwert und die erste unterstützte Version von Visual Studio angezeigt:

| Regelname | Anzuwendende Sprachen | Visual Studio-Standard | Visual Studio 2017 |
| ----------- | -------------------- | ----------------------| ---------------- |
| dotnet_sort_system_directives_first | C# und Visual Basic | true | 15.3 |
| dotnet_separate_import_directive_groups | C# und Visual Basic | False | 15.5 |

**dotnet\_sort\_system\_directives_first**

- Wenn diese Regel auf **TRUE** festgelegt ist, werden System.* using-Direktiven alphabetisch sortiert und vor anderen using-Direktiven platziert.
- Wenn diese Regel auf **FALSE** festgelegt ist, werden keine System.* using-Direktiven vor anderen using-Direktiven platziert.

Codebeispiele:

```csharp
// dotnet_sort_system_directives_first = true
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;

// dotnet_sort_system_directives_first = false
using System.Collections.Generic;
using Octokit;
using System.Threading.Tasks;
```

*EDITORCONFIG-Beispieldatei:*

```EditorConfig
# .NET formatting settings:
[*.{cs,vb}]
dotnet_sort_system_directives_first = true
```

**dotnet\_separate\_import\_directive\_groups**

- Wenn diese Regel auf **TRUE** festgelegt ist, fügen Sie eine leere Zeile zwischen Using-Anweisungsgruppen ein.
- Wenn diese Regel auf **FALSE** festgelegt ist, fügen Sie keine leere Zeile zwischen Using-Anweisungsgruppen ein.

Codebeispiele:

```csharp
// dotnet_separate_import_directive_groups = true
using System.Collections.Generic;
using System.Threading.Tasks;

using Octokit;

// dotnet_separate_import_directive_groups = false
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;
```

*EDITORCONFIG-Beispieldatei:*

```EditorConfig
# .NET formatting settings:
[*.{cs,vb}]
dotnet_separate_import_directive_groups = true
```

### <a name="c-formatting-settings"></a>C#-Formatierungseinstellungen

Die Formatierungsregeln in diesem Abschnitt gelten nur für C#-Code.

#### <a name="newline"></a>Newline-Optionen

Diese Formatierungsregeln beziehen sich auf die Verwendung neuer Zeilen zur Codeformatierung.

In der folgenden Tabelle werden die Regelnamen für „neue Zeile“, anzuwendende Sprachen, Standardwerte und die erste unterstützte Version von Visual Studio angezeigt:

| Regelname | Anzuwendende Sprachen | Visual Studio-Standard | Visual Studio 2017 |
| ----------- | -------------------- | ----------------------| ---------------- |
| csharp_new_line_before_open_brace | C# | alle | 15.3 |
| csharp_new_line_before_else | C# | true | 15.3 |
| csharp_new_line_before_catch | C# | true | 15.3 |
| csharp_new_line_before_finally | C# | true | 15.3 |
| csharp_new_line_before_members_in_object_initializers | C# | true | 15.3 |
| csharp_new_line_before_members_in_anonymous_types | C# | true | 15.3 |
| csharp_new_line_between_query_expression_clauses | C# | true | 15.3 |

**csharp\_new\_line\_before\_open_brace**

Diese Regel bezieht sich auf die Frage, ob eine öffnende geschweifte Klammer `{` in derselben Zeile wie der vorangehende Code oder in einer neuen Zeile platziert werden soll. Bei dieser Regel geben Sie nicht **TRUE** oder **FALSE** an. Stattdessen geben Sie **Alle**, **Keine** oder mindestens ein Codeelement an, wie z.B. **Methoden** oder **Eigenschaften**, um festzulegen, wann diese Regel angewendet werden sollte. Die vollständige Liste der zulässigen Werte wird in der folgenden Tabelle dargestellt:

| Wert | Beschreibung
| ------------- |:-------------|
| accessors, anonymous_methods, anonymous_types, control_blocks, events, indexers, lambdas, local_functions, methods, object_collection_array_initializers, properties, types.<br>(Trennen Sie mehrere Arten mit einem Komma). | Klammern müssen für die angegebenen Codeelemente in einer neuen Zeile stehen (Stil „Allman“) |
| alle | Klammern müssen für alle Ausdrücke in einer neuen Zeile stehen (Stil „Allman“) |
| Keine | Klammern müssen für alle Ausdrücke in der gleichen Zeile stehen („K&R“) |

Codebeispiele:

```csharp
// csharp_new_line_before_open_brace = all
void MyMethod()
{
    if (...)
    {
        ...
    }
}

// csharp_new_line_before_open_brace = none
void MyMethod() {
    if (...) {
        ...
    }
}
```

**csharp\_new\_line\_before_else**

- Wenn diese Regel auf **TRUE** festgelegt ist, werden `else`-Anweisungen in einer neuen Zeile platziert.
- Wenn diese Regel auf **FALSE** festgelegt ist, werden `else`-Anweisungen in derselben Zeile platziert.

Codebeispiele:

```csharp
// csharp_new_line_before_else = true
if (...) {
    ...
}
else {
    ...
}

// csharp_new_line_before_else = false
if (...) {
    ...
} else {
    ...
}
```

**csharp\_new\_line\_before_catch**

- Wenn diese Regel auf **TRUE** festgelegt ist, werden `catch`-Anweisungen in einer neuen Zeile platziert.
- Wenn diese Regel auf **FALSE** festgelegt ist, werden `catch`-Anweisungen in derselben Zeile platziert.

Codebeispiele:

```csharp
// csharp_new_line_before_catch = true
try {
    ...
}
catch (Exception e) {
    ...
}

// csharp_new_line_before_catch = false
try {
    ...
} catch (Exception e) {
    ...
}
```

**csharp\_new\_line\_before_finally**

- Wenn diese Regel auf **TRUE** festgelegt ist, müssen `finally`-Anweisungen in einer neuen Zeile hinter der schließenden geschweiften Klammer stehen.
- Wenn diese Regel auf **FALSE** festgelegt ist, müssen `finally`-Anweisungen in derselben Zeile wie die schließende geschweifte Klammer stehen.

Codebeispiele:

```csharp
// csharp_new_line_before_finally = true
try {
    ...
}
catch (Exception e) {
    ...
}
finally {
    ...
}

// csharp_new_line_before_finally = false
try {
    ...
} catch (Exception e) {
    ...
} finally {
    ...
}
```

**csharp\_new\_line\_before\_members\_in\_object_initializers**

- Wenn diese Regel auf **TRUE** festgelegt ist, müssen Member von Objektinitialisierern in separaten Zeilen aufgeführt werden.
- Wenn diese Regel auf **FALSE** festgelegt ist, müssen Member von Objektinitialisierern in derselben Zeile stehen.

Codebeispiele:

```csharp
// csharp_new_line_before_members_in_object_initializers = true
var z = new B()
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_object_initializers = false
var z = new B()
{
    A = 3, B = 4
}
```

**csharp\_new\_line\_before\_members\_in\_anonymous_types**

- Wenn diese Regel auf **TRUE** festgelegt ist, müssen Member von anonymen Typen in separaten Zeilen stehen.
- Wenn diese Regel auf **FALSE** festgelegt ist, müssen Member von anonymen Typen in derselben Zeile stehen.

Codebeispiele:

```csharp
// csharp_new_line_before_members_in_anonymous_types = true
var z = new
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_anonymous_types = false
var z = new
{
    A = 3, B = 4
}
```

**csharp_new_line_between_query_expression_clauses**

- Wenn diese Regel auf **TRUE** festgelegt ist, müssen Elemente von Abfrageausdrucksklauseln in separaten Zeilen stehen.
- Wenn diese Regel auf **FALSE** festgelegt ist, müssen Elemente von Abfrageausdrucksklauseln in derselben Zeile stehen.

Codebeispiele:

```csharp
// csharp_new_line_between_query_expression_clauses = true
var q = from a in e
        from b in e
        select a * b;

// csharp_new_line_between_query_expression_clauses = false
var q = from a in e from b in e
        select a * b;
```

*EDITORCONFIG-Beispieldatei:*

```EditorConfig
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_open_brace = methods, properties, control_blocks, types
csharp_new_line_before_else = true
csharp_new_line_before_catch = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_between_query_expression_clauses = true
```

#### <a name="indent"></a>Einzugsoptionen

Diese Formatierungsregeln beziehen sich auf die Verwendung von Einzügen zur Codeformatierung.

In der folgenden Tabelle werden die Regelnamen, anzuwendende Sprachen, Standardwerte und die erste unterstützte Version von Visual Studio angezeigt:

| Regelname | Anzuwendende Sprachen | Visual Studio-Standard | Visual Studio 2017 |
| ----------- | -------------------- | ----------------------| ---------------- |
| csharp_indent_case_contents | C# | true | 15.3 |
| csharp_indent_switch_labels | C# | true | 15.3 |
| csharp_indent_labels | C# | no_change | 15.3 |

**csharp\_indent\_case_contents**

- Wenn diese Regel auf **TRUE** festgelegt ist, werden die `switch`-Fallinhalte eingezogen.
- Wenn diese Regel auf **FALSE** festgelegt ist, werden die `switch`-Fallinhalte nicht eingezogen.

Codebeispiele:

```csharp
// csharp_indent_case_contents = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_case_contents = false
switch(c) {
    case Color.Red:
    Console.WriteLine("The color is red");
    break;
    case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
    default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

**csharp\_indent\_switch_labels**

- Wenn diese Regel auf **TRUE** festgelegt ist, werden die `switch`-Bezeichnungen eingezogen.
- Wenn diese Regel auf **FALSE** festgelegt ist, werden die `switch`-Bezeichnungen nicht eingezogen.

Codebeispiele:

```csharp
// csharp_indent_switch_labels = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_switch_labels = false
switch(c) {
case Color.Red:
    Console.WriteLine("The color is red");
    break;
case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

**csharp\_indent_labels**

Diese Regel akzeptiert nicht den Wert **TRUE** oder **FALSE**, sondern einen Wert aus der folgenden Tabelle:

| Wert | Beschreibung |
| ----- |:----------- |
| flush_left | Bezeichnungen werden in der Spalte ganz links angeordnet |
| one_less_than_current | Bezeichnungen werden mit geringerem Einzug platziert als der aktuelle Kontext. |
| no_change | Bezeichnungen werden mit dem gleichen Einzug platziert wie der aktuelle Kontext. |

Codebeispiele:

```csharp
// csharp_indent_labels= flush_left
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
error:
        throw new Exception(...);
    }
}

// csharp_indent_labels = one_less_than_current
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
    error:
        throw new Exception(...);
    }
}

// csharp_indent_labels= no_change
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
        error:
        throw new Exception(...);
    }
}
```

*EDITORCONFIG-Beispieldatei:*

```EditorConfig
# CSharp formatting settings:
[*.cs]
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left
```

#### <a name="spacing"></a>Abstandsoptionen

Diese Formatierungsregeln beziehen sich auf die Verwendung von Leerzeichen zur Codeformatierung.

In der folgenden Tabelle werden die Regelnamen, anzuwendende Sprachen, Standardwerte und die erste unterstützte Version von Visual Studio angezeigt:

| Regelname | Anzuwendende Sprachen | Visual Studio-Standard | Visual Studio 2017 |
| ----------- | -------------------- | ----------------------| ---------------- |
| csharp_space_after_cast | C# | False | 15.3 |
| csharp_space_after_keywords_in_control_flow_statements | C# | true | 15.3 |
| csharp_space_between_method_declaration_parameter_list_parentheses | C# | False | 15.3 |
| csharp_space_between_method_call_parameter_list_parentheses | C# | False | 15.3 |
| csharp_space_between_parentheses | C# | False | 15.3 |
| csharp_space_before_colon_in_inheritance_clause | C# | true | 15.7 |
| csharp_space_after_colon_in_inheritance_clause | C# | true | 15.7 |
| csharp_space_around_binary_operators | C# | before_and_after | 15.7 |
| csharp_space_between_method_declaration_empty_parameter_list_parentheses | C# | False | 15.7 |
| csharp_space_between_method_call_name_and_opening_parenthesis | C# | False | 15.7 |
| csharp_space_between_method_call_empty_parameter_list_parentheses | C# | False | 15.7 |

**csharp\_space\_after_cast**

- Wenn diese Regel auf **TRUE** festgelegt ist, ist zwischen einer Typumwandlung und dem Wert ein Leerzeichen erforderlich.
- Wenn diese Regel auf **FALSE** festgelegt ist, ist zwischen einer Typumwandlung und dem Wert _kein_ Leerzeichen erforderlich.

Codebeispiele:

```csharp
// csharp_space_after_cast = true
int y = (int) x;

// csharp_space_after_cast = false
int y = (int)x;
```

**csharp_space_after_keywords_in_control_flow_statements**

- Wenn diese Regel auf **TRUE** festgelegt ist, ist hinter einem Schlüsselwort in einer Ablaufsteuerungsanweisung ein Leerzeichen erforderlich, z.B. in einer `for`-Schleife.
- Wenn diese Regel auf **FALSE** festgelegt ist, ist hinter einem Schlüsselwort in einer Ablaufsteuerungsanweisung _kein_ Leerzeichen erforderlich, z.B. in einer `for`-Schleife.

Codebeispiele:

```csharp
// csharp_space_after_keywords_in_control_flow_statements = true
for (int i;i<x;i++) { ... }

// csharp_space_after_keywords_in_control_flow_statements = false
for(int i;i<x;i++) { ... }
```

**csharp_space_between_method_declaration_parameter_list_parentheses**

- Wenn diese Regel auf **TRUE** festgelegt ist, platzieren Sie bei einer Parameterliste der Methodendeklaration hinter der öffnenden Klammer und vor der schließenden Klammer ein Leerzeichen.
- Wenn diese Regel auf **FALSE** festgelegt ist, platzieren Sie bei einer Parameterliste der Methodendeklaration hinter der öffnenden Klammer und vor der schließenden Klammer kein Leerzeichen.

Codebeispiele:

```csharp
// csharp_space_between_method_declaration_parameter_list_parentheses = true
void Bark( int x ) { ... }

// csharp_space_between_method_declaration_parameter_list_parentheses = false
void Bark(int x) { ... }
```

**csharp_space_between_method_call_parameter_list_parentheses**

- Wenn diese Regel auf **TRUE** festgelegt ist, platzieren Sie bei einem Methodenaufruf hinter der öffnenden Klammer und vor der schließenden Klammer ein Leerzeichen.
- Wenn diese Regel auf **FALSE** festgelegt ist, platzieren Sie bei einem Methodenaufruf hinter der öffnenden Klammer und vor der schließenden Klammer kein Leerzeichen.

Codebeispiele:

```csharp
// csharp_space_between_method_call_parameter_list_parentheses = true
MyMethod( argument );

// csharp_space_between_method_call_parameter_list_parentheses = false
MyMethod(argument);
```

**csharp_space_between_parentheses**

Diese Regel akzeptiert mindestens einen Wert aus der folgenden Tabelle:

| Wert | Beschreibung |
| ----- |:------------|
| control_flow_statements | Leerzeichen zwischen Klammern von Ablaufsteuerungsanweisungen einfügen. |
| Ausdrücke | Leerzeichen zwischen Klammern von Ausdrücken einfügen. |
| type_casts | Leerzeichen zwischen Klammern in Typumwandlungen einfügen. |

Wenn Sie diese Regel auslassen oder einen anderen Wert als `control_flow_statements`, `expressions` oder `type_casts` verwenden, wird die Einstellung nicht angewendet.

Codebeispiele:

```csharp
// csharp_space_between_parentheses = control_flow_statements
for ( int i = 0; i < 10; i++ ) { }

// csharp_space_between_parentheses = expressions
var z = ( x * y ) - ( ( y - x ) * 3 );

// csharp_space_between_parentheses = type_casts
int y = ( int )x;
```

**csharp\_space\_before\_colon\_in\_inheritance_clause**

- Wenn diese Regel auf **TRUE** festgelegt ist, ist vor dem Doppelpunkt für Basen und Schnittstellen in einer Typdeklaration ein Leerzeichen erforderlich.
- Wenn diese Regel auf **FALSE** festgelegt ist, ist vor dem Doppelpunkt für Basen und Schnittstellen in einer Typdeklaration _kein_ Leerzeichen erforderlich.

Codebeispiele:

```csharp
// csharp_space_before_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_before_colon_in_inheritance_clause = false
interface I
{

}

class C: I
{

}
```

**csharp\_space\_after\_colon\_in\_inheritance_clause**

- Wenn diese Regel auf **TRUE** festgelegt ist, ist nach dem Doppelpunkt für Basen und Schnittstellen in einer Typdeklaration ein Leerzeichen erforderlich.
- Wenn diese Regel auf **FALSE** festgelegt ist, ist nach dem Doppelpunkt für Basen und Schnittstellen in einer Typdeklaration _kein_ Leerzeichen erforderlich.

Codebeispiele:

```csharp
// csharp_space_after_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_after_colon_in_inheritance_clause = false
interface I
{

}

class C :I
{

}
```

**csharp\_space\_around\_binary_operators**

Diese Regel akzeptiert einen Wert aus der folgenden Tabelle:

| Wert | Beschreibung |
| ----- |:------------|
| before_and_after | Leerzeichen vor und nach dem binären Operator einfügen |
| Keine | Leerzeichen vor und nach dem binären Operator entfernen |
| Ignorieren | Leerzeichen um binäre Operatoren ignorieren |

Wenn Sie diese Regel auslassen oder einen anderen Wert als `before_and_after`, `none` oder `ignore` verwenden, wird die Einstellung nicht angewendet.

Codebeispiele:

```csharp
// csharp_space_around_binary_operators = before_and_after
return x * (x - y);

// csharp_space_around_binary_operators = none
return x*(x-y);

// csharp_space_around_binary_operators = ignore
return x  *  (x-y);
```

**csharp_space_between_method_declaration_empty_parameter_list_parentheses**

- Wenn diese Regel auf **TRUE** festgelegt ist, fügen Sie bei einer Methodendeklaration innerhalb der runden Klammern um eine leere Parameterliste ein Leerzeichen ein.
- Wenn diese Regel auf **FALSE** festgelegt ist, entfernen Sie bei einer Methodendeklaration innerhalb der runden Klammern um eine leere Parameterliste ein Leerzeichen.

Codebeispiele:

```csharp
// csharp_space_between_method_declaration_empty_parameter_list_parentheses = true
void Goo( )
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}

// csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

**csharp_space_between_method_call_name_and_opening_parenthesis**

- Wenn diese Regel auf **TRUE** festgelegt ist, fügen Sie zwischen dem Namen des Methodenaufrufs und der öffnenden Klammer ein Leerzeichen ein.
- Wenn diese Regel auf **FALSE** festgelegt ist, entfernen Sie zwischen dem Namen des Methodenaufrufs und der öffnenden Klammer ein Leerzeichen.

Codebeispiele:

```csharp
// csharp_space_between_method_call_name_and_opening_parenthesis = true
void Goo()
{
    Goo (1);
}

void Goo(int x)
{
    Goo ();
}

// csharp_space_between_method_call_name_and_opening_parenthesis = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

**csharp_space_between_method_call_empty_parameter_list_parentheses**

- Wenn diese Regel auf **TRUE** festgelegt ist, fügen Sie innerhalb der runden Klammern um eine leere Argumentliste ein Leerzeichen ein.
- Wenn diese Regel auf **FALSE** festgelegt ist, entfernen Sie innerhalb der runden Klammern um eine leere Argumentliste ein Leerzeichen.

Codebeispiele:

```csharp
// csharp_space_between_method_call_empty_parameter_list_parentheses = true
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo( );
}

// csharp_space_between_method_call_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

*EDITORCONFIG-Beispieldatei:*

```EditorConfig
# CSharp formatting settings:
[*.cs]
csharp_space_after_cast = true
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_between_method_declaration_parameter_list_parentheses = true
csharp_space_between_method_call_parameter_list_parentheses = true
csharp_space_between_parentheses = control_flow_statements, type_casts
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_around_binary_operators = before_and_after
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_between_method_call_empty_parameter_list_parentheses = false
```

#### <a name="wrapping"></a>Umbruchoptionen

Diese Formatierungsregeln beziehen sich auf die Verwendung von einzelnen Zeilen im Vergleich zu separaten Zeilen bei Anweisungen und Codeblöcken.

In der folgenden Tabelle werden die Regelnamen, anzuwendende Sprachen, Standardwerte und die erste unterstützte Version von Visual Studio angezeigt:

| Regelname | Anzuwendende Sprachen | Visual Studio-Standard | Visual Studio 2017 |
| ----------- | -------------------- | ----------------------| ---------------- |
| csharp_preserve_single_line_statements | C# | true | 15.3 |
| csharp_preserve_single_line_blocks | C# | true | 15.3 |

**csharp_preserve_single_line_statements**

- Wenn diese Regel auf **TRUE** festgelegt ist, werden Anweisungen und Memberdeklarationen in derselben Zeile belassen.
- Wenn diese Regel auf **FALSE** festgelegt ist, werden Anweisungen und Memberdeklarationen in unterschiedlichen Zeilen belassen.

Codebeispiele:

```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";

//csharp_preserve_single_line_statements = false
int i = 0;
string name = "John";
```

**csharp_preserve_single_line_blocks**

- Wenn diese Regel auf **TRUE** festgelegt ist, wird der Codeblock in einer einzelnen Zeile belassen.
- Wenn diese Regel auf **FALSE** festgelegt ist, wird der Codeblock in separaten Zeilen belassen.

Codebeispiele:

```csharp
//csharp_preserve_single_line_blocks = true
public int Foo { get; set; }

//csharp_preserve_single_line_blocks = false
public int MyProperty
{
    get; set;
}
```

*EDITORCONFIG-Beispieldatei:*

```EditorConfig
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true
```

## <a name="example-editorconfig-file"></a>EDITORCONFIG-Beispieldatei

Im Folgenden finden Sie eine *EDITORCONFIG*-Beispieldatei mit den Standardoptionen für die ersten Schritte:

```EditorConfig
###############################
# Core EditorConfig Options   #
###############################

root = true

# All files
[*]
indent_style = space

# Code files
[*.{cs,csx,vb,vbx}]
indent_size = 4
insert_final_newline = true
charset = utf-8-bom

###############################
# .NET Coding Conventions     #
###############################

[*.{cs,vb}]
# Organize usings
dotnet_sort_system_directives_first = true
dotnet_separate_import_directive_groups = false

# this. preferences
dotnet_style_qualification_for_field = false:silent
dotnet_style_qualification_for_property = false:silent
dotnet_style_qualification_for_method = false:silent
dotnet_style_qualification_for_event = false:silent

# Language keywords vs BCL types preferences
dotnet_style_predefined_type_for_locals_parameters_members = true:silent
dotnet_style_predefined_type_for_member_access = true:silent

# Parentheses preferences
dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_operators = never_if_unnecessary:silent

# Modifier preferences
dotnet_style_require_accessibility_modifiers = for_non_interface_members:silent
dotnet_style_readonly_field = true:suggestion

# Expression-level preferences
dotnet_style_object_initializer = true:suggestion
dotnet_style_collection_initializer = true:suggestion
dotnet_style_explicit_tuple_names = true:suggestion
dotnet_style_null_propagation = true:suggestion
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_prefer_is_null_check_over_reference_equality_method = true:silent
dotnet_style_prefer_inferred_tuple_names = true:suggestion
dotnet_style_prefer_inferred_anonymous_type_member_names = true:suggestion
dotnet_style_prefer_auto_properties = true:silent
dotnet_style_prefer_conditional_expression_over_assignment = true:silent
dotnet_style_prefer_conditional_expression_over_return = true:silent

###############################
# Naming Conventions          #
###############################

# Style Definitions
dotnet_naming_style.pascal_case_style.capitalization             = pascal_case

# Use PascalCase for constant fields
dotnet_naming_rule.constant_fields_should_be_pascal_case.severity = suggestion
dotnet_naming_rule.constant_fields_should_be_pascal_case.symbols  = constant_fields
dotnet_naming_rule.constant_fields_should_be_pascal_case.style    = pascal_case_style
dotnet_naming_symbols.constant_fields.applicable_kinds            = field
dotnet_naming_symbols.constant_fields.applicable_accessibilities  = *
dotnet_naming_symbols.constant_fields.required_modifiers          = const

###############################
# C# Code Style Rules         #
###############################

[*.cs]
# var preferences
csharp_style_var_for_built_in_types = true:silent
csharp_style_var_when_type_is_apparent = true:silent
csharp_style_var_elsewhere = true:silent

# Expression-bodied members
csharp_style_expression_bodied_methods = false:silent
csharp_style_expression_bodied_constructors = false:silent
csharp_style_expression_bodied_operators = false:silent
csharp_style_expression_bodied_properties = true:silent
csharp_style_expression_bodied_indexers = true:silent
csharp_style_expression_bodied_accessors = true:silent

# Pattern-matching preferences
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion

# Null-checking preferences
csharp_style_throw_expression = true:suggestion
csharp_style_conditional_delegate_call = true:suggestion

# Modifier preferences
csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async:suggestion

# Expression-level preferences
csharp_prefer_braces = true:silent
csharp_style_deconstructed_variable_declaration = true:suggestion
csharp_prefer_simple_default_expression = true:suggestion
csharp_style_pattern_local_over_anonymous_function = true:suggestion
csharp_style_inlined_variable_declaration = true:suggestion

###############################
# C# Formatting Rules         #
###############################

# New line preferences
csharp_new_line_before_open_brace = all
csharp_new_line_before_else = true
csharp_new_line_before_catch = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_between_query_expression_clauses = true

# Indentation preferences
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left

# Space preferences
csharp_space_after_cast = false
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_between_method_call_parameter_list_parentheses = false
csharp_space_between_method_declaration_parameter_list_parentheses = false
csharp_space_between_parentheses = false
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_around_binary_operators = before_and_after
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_between_method_call_empty_parameter_list_parentheses = false

# Wrapping preferences
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true

##################################
# Visual Basic Code Style Rules  #
##################################

[*.vb]
# Modifier preferences
visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async:suggestion
```

## <a name="see-also"></a>Siehe auch

- [Schnelle Aktionen](../ide/quick-actions.md)
- [.NET-Namenskonventionen für EditorConfig](../ide/editorconfig-naming-conventions.md)
- [Erstellen portierbarer benutzerdefinierter Editor-Optionen](../ide/create-portable-custom-editor-options.md)
- [.editorconfig-Datei der .NET Compiler Platform](https://github.com/dotnet/roslyn/blob/master/.editorconfig)
