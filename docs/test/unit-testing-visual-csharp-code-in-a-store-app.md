---
title: Komponententests in Visual C#-Code
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- uwp
author: gewarren
ms.openlocfilehash: 359f2f8b078c197f12a6db09858ca7c9da5a621a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62809631"
---
# <a name="unit-test-c-code"></a>Komponententest von C#-Code

In diesem Artikel wird eine Möglichkeit zum Erstellen von Komponententests für eine C#-Klasse in einer UWP-App beschrieben. Die Klasse "Rooter" implementiert eine Funktion zum näherungsweisen Berechnen der Quadratwurzel einer vorgegebenen Zahl, und zwar in einer Weise, die entfernt an Grenzwertberechnungen in der Analysis erinnert. Von der Mathematik-App kann diese Funktion dann verwendet werden, um Benutzern zu zeigen, wie interessant und unterhaltsam Mathematik sein kann.

In diesem Artikel wird gezeigt, wie Komponententests als erster Schritt in der Entwicklung verwendet werden. Bei dieser Vorgehensweise schreiben Sie zuerst eine Testmethode, die ein bestimmtes Verhalten in Ihrem Testsystem überprüft. Anschließend schreiben Sie den Code, der im Test erfolgreich ist. Durch das Ändern der Reihenfolge bei den folgenden Prozeduren, können Sie diese Strategie umkehren und zuerst den zu testenden Code und anschließend die Komponententests schreiben.

In diesem Artikel werden auch eine einzelne Visual Studio-Projektmappe und separate Projekte für die zu testenden Komponententests und DLLs erstellt. Sie können die Komponententests auch direkt in das DLL-Projekt einfügen, oder Sie können separate Lösungen für die Komponententests und die DLL erstellen.

## <a name="create-the-solution-and-the-unit-test-project"></a>Erstellen Sie die Projektmappe und das Komponententestprojekt.

1. Wählen Sie im Menü **Datei** die Optionsfolge **Neu** > **Projekt** aus.

2. Suchen Sie die Projektvorlage **Leere App (universelles Windows)**, und wählen Sie sie aus.

3. Benennen Sie das Projekt mit `Maths`.

4. Wählen Sie im **Projektmappen-Explorer** den Projektmappennamen aus. Wählen Sie anschließend aus dem Kontextmenü die Option **Hinzufügen** > **Neues Projekt** aus.

5. Suchen Sie die Projektvorlage **Komponententest-App (Universelles Windows)**, und wählen Sie sie aus.

6. Öffnen Sie *UnitTest1.cs* im Visual Studio-Editor.

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using System.Text;
   using Microsoft.VisualStudio.TestTools.UnitTesting;
   using Maths;

   namespace RooterTests
   {
       [TestClass]
       public class UnitTest1

           [TestMethod]
           public void TestMethod1()
           {

           }
   ```

   Hinweis:

   - Jeder Test wird durch die Verwendung des <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>-Attributs definiert. Eine Testmethode muss den Wert "void" zurückgeben und darf keine Parameter haben.

   - Testmethoden müssen in einer Klasse enthalten sein, die durch das <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>-Attribut ergänzt wird.

        Wenn die Tests ausgeführt werden, wird eine Instanz jeder Testklasse erstellt. Die Testmethoden werden in einer nicht vorgegebenen Reihenfolge aufgerufen.

   - Sie können spezielle Methoden definieren, die vor und nach jedem Modul, jeder Klasse oder Methode aufgerufen werden. Weitere Informationen finden Sie unter [Verwenden des MSTest-Frameworks in Komponententests](../test/using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md).

## <a name="verify-that-the-tests-run-in-test-explorer"></a>Stellen Sie sicher, dass die Tests im Test-Explorer ausgeführt werden.

1. Fügen Sie in Datei *UnitTest1.cs* einen Testcode in „TestMethod1“ hinzu:

   ```csharp
   [TestMethod]
   public void TestMethod1()
   {
       Assert.AreEqual(0, 0);
   }
   ```

   Beachten Sie, dass die <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> -Klasse mehrere statische Methoden zur Verfügung stellt, die Sie verwenden können, um Ergebnisse in den Testmethoden zu überprüfen.

2. Wählen Sie im Menü **Test** die Option **Ausführen** und dann **Alle ausführen** aus.

   Das Testprojekt wird erstellt und ausgeführt. Das Fenster **Test-Explorer** wird angezeigt, und der Test wird unter **Bestandene Tests** aufgeführt. Unten im Fenster im Bereich **Zusammenfassung** werden weitere Informationen zum ausgewählten Test angezeigt.

   ![Test-Explorer](../test/media/ute_cpp_testexplorer_testmethod1.png)

## <a name="add-the-rooter-class-to-the-maths-project"></a>Fügen Sie die Klasse "Rooter" zu dem Projekt "Mathematik" hinzu.

1. Wählen Sie im **Projektmappen-Explorer** den Projektnamen **Maths** aus. Wählen Sie im Kontextmenü **Hinzufügen** und dann **Klasse** aus.

2. Geben Sie der Klassendatei den Namen *Rooter.cs*.

3. Fügen Sie der Rooter-Klassendatei *Rooter.cs* den folgenden Code hinzu:

   ```csharp
   public Rooter()
   {
   }

   // estimate the square root of a number
   public double SquareRoot(double x)
   {
       return 0.0;
   }
   ```

   Die `Rooter`-Klasse deklariert einen Konstruktor und die `SquareRoot`-Abschätzermethode.

4. Die `SquareRoot`-Methode ist nur eine minimale Implementierung, die gerade ausreicht, um die Grundstruktur des Testsetups zu testen.

## <a name="couple-the-test-project-to-the-app-project"></a>Verknüpfen Sie das Testprojekt mit dem App-Projekt.

1. Fügen Sie dem RooterTests-Projekt einen Verweis auf die Mathematik-App hinzu.

    1. Wählen Sie im **Projektmappen-Explorer** das Projekt **RooterTests** und anschließend im Kontextmenü die Option **Verweis hinzufügen** aus.

    2. Erweitern Sie im Dialogfeld **Verweis hinzufügen - RooterTests** den Eintrag **Projektmappe**, und wählen Sie **Projekte** aus. Wählen Sie dann das Element **Mathematik** aus.

        ![Einen Verweis zum Projekt "Maths" hinzufügen](../test/media/ute_cs_windows_addreference.png)

2. Fügen Sie der Datei *UnitTest1.cs* eine using-Anweisung hinzu:

    1. Öffnen Sie *UnitTest1.cs*.

    2. Fügen Sie diesen Code unter der Zeile `using Microsoft.VisualStudio.TestTools.UnitTesting;` hinzu:

       ```csharp
       using Maths;
       ```

3. Fügen Sie einen Test hinzu, der die Funktion "Rooter" verwendet. Fügen Sie *UnitTest1.cs* den folgenden Code hinzu:

   ```csharp
   [TestMethod]
   public void BasicTest()
   {
       Maths.Rooter rooter = new Rooter();
       double expected = 0.0;
       double actual = rooter.SquareRoot(expected * expected);
       double tolerance = .001;
       Assert.AreEqual(expected, actual, tolerance);
   }
   ```

4. Erstellen Sie die Projektmappe.

   Der neue Test wird im **Test-Explorer** im Knoten **Nicht ausgeführte Tests** angezeigt.

5. Wählen Sie im **Test-Explorer** die Option **Alle ausführen** aus.

   ![Einfacher Test bestanden](../test/media/ute_cpp_testexplorer_basictest.png)

Sie haben den Test und die Codeprojekte eingerichtet und überprüft, dass Sie Tests ausführen können, die Funktionen im Codeprojekt ausführen. Jetzt können Sie beginnen, echte Tests und Code zu schreiben.

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a>Die Tests iterativ steigern und erfolgreich abschließen

1. Fügen Sie einen neuen Test hinzu:

   ```csharp
   [TestMethod]
   public void RangeTest()
   {
       Rooter rooter = new Rooter();
       for (double v = 1e-6; v < 1e6; v = v * 3.2)
       {
           double expected = v;
           double actual = rooter.SquareRoot(v*v);
           double tolerance = ToleranceHelper(expected);
           Assert.AreEqual(expected, actual, tolerance);
       }
   }
   ```

   > [!TIP]
   > Es wird empfohlen, keine Tests zu ändern, die erfolgreich abgeschlossen wurden. Fügen Sie stattdessen einen neuen Test hinzu, aktualisieren Sie den Code, damit der Test erfolgreich ist, und fügen Sie dann einen weiteren Test hinzu, usw.
   >
   > Wenn Benutzer ihre Anforderungen ändern, deaktivieren Sie die Tests, die nicht mehr richtig sind. Schreiben Sie neue Tests und führen Sie diese jeweils nacheinander auf dieselbe inkrementelle Weise durch.

2. Wählen Sie im **Test-Explorer** die Option **Alle ausführen** aus.

3. Der Test schlägt fehl.

   ![Fehler beim RangeTest](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

   > [!TIP]
   > Überprüfen Sie unmittelbar nach dem Schreiben eines Tests, dass er fehlschlägt. Dadurch können Sie vermeiden, dass Sie einen Test schreiben, bei dessen Ausführung nie ein Fehler auftritt.

4. Erweitern Sie den Code unter dem Test, damit der neue Test erfolgreich ist. Ändern Sie die `SquareRoot`-Funktion in *Rooter.cs* zu Folgendem:

   ```csharp
   public double SquareRoot(double x)
   {
       double estimate = x;
       double diff = x;
       while (diff > estimate / 1000)
       {
           double previousEstimate = estimate;
           estimate = estimate - (estimate * estimate - x) / (2 * estimate);
           diff = Math.Abs(previousEstimate - estimate);
       }
       return estimate;
   }
   ```

5. Erstellen Sie die Projektmappe, und wählen Sie dann im **Test-Explorer** die Option **Alle ausführen** aus.

   Alle drei Tests sind jetzt erfolgreich.

> [!TIP]
> Entwickeln Sie Code, indem Sie währenddessen Tests hinzufügen. Stellen Sie sicher, dass alle Tests nach jeder Iteration erfolgreich sind.

## <a name="debug-a-failing-test"></a>Einen nicht bestandenen Test debuggen

1. Fügen Sie einen anderen Test zu *UnitTest1.cpp* hinzu:

    ```csharp
    // Verify that negative inputs throw an exception.
    [TestMethod]
    public void NegativeRangeTest()
    {
        string message;
        Rooter rooter = new Rooter();
        for (double v = -0.1; v > -3.0; v = v - 0.5)
        {
            try
            {
                // Should raise an exception:
                double actual = rooter.SquareRoot(v);

                message = String.Format("No exception for input {0}", v);
                Assert.Fail(message);
            }
            catch (ArgumentOutOfRangeException ex)
            {
                continue; // Correct exception.
            }
            catch (Exception e)
            {
                message = String.Format("Incorrect exception for {0}", v);
                Assert.Fail(message);
            }
        }
    }
    ```

2. Wählen Sie im **Test-Explorer** die Option **Alle ausführen** aus.

   Der Test schlägt fehl. Wählen Sie den Testnamen im **Test-Explorer** aus. Die Assertation, bei der ein Fehler aufgetreten ist, wird gekennzeichnet. Die Fehlermeldung wird im Detailbereich vom **Test-Explorer** angezeigt.

   ![Fehler bei NegativeRangeTests](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png)

3. Um zu sehen, warum der Test nicht erfolgreich war, führen Sie schrittweise die Funktion aus:

    1. Legen Sie einen Haltepunkt am Anfang der `SquareRoot`-Funktion fest.

    2. Wählen Sie im Kontextmenü des nicht erfolgreichen Tests **Ausgewählte Tests debuggen**.

        Wenn die Ausführung am Haltepunkt angehalten wird, führen Sie den Code schrittweise aus.

    3. Fügen Sie Code zur Rooter-Methode hinzu, um die Ausnahme zu erfassen:

        ```csharp
        public double SquareRoot(double x)
        {
            if (x < 0.0)
            {
                throw new ArgumentOutOfRangeException();
        }
        ```

4. Klicken Sie im **Test-Explorer** auf **Alle ausführen**, um die korrigierte Methode zu testen und sicherzustellen, dass Sie keine Regression eingeführt haben.

Alle Tests sind nun erfolgreich.

![Alle Tests erfolgreich](../test/media/ute_ult_alltestspass.png)

## <a name="refactor-the-code"></a>Gestalten Sie den Code um.

**Vereinfachen Sie die zentrale Berechnung in der SquareRoot-Funktion:**

1. Ändern Sie die Ergebnisimplementierung.

    ```csharp
    // old code
    //result = result - (result*result - v)/(2*result);
    // new code
    result = (result + v/result) / 2.0;
    ```

2. Wählen Sie **Alle ausführen** aus, um die umgestaltete Methode zu testen und zu überprüfen, dass Sie keine Regression eingeführt haben.

> [!TIP]
> Mit einem stabilen Satz guter Komponententests haben Sie mehr Gewissheit, dass Sie beim Ändern des Codes keine Fehler eingeführt haben.

**Gestalten Sie den Testcode um, um doppelten Code zu vermeiden.**

Die `RangeTest`-Methode weist dem Nenner der `tolerance`-Variablen, die der <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>-Methode übergeben wird, vordefinierten Code zu. Wenn Sie zusätzliche Tests hinzufügen möchten, in denen die gleiche Toleranzberechnung zur Anwendung kommt, können Fehler auftreten, wenn ein vordefinierter Wert an mehreren Speicherorten verwendet wird.

1. Fügen Sie der Unit1Test-Klasse eine private Methode hinzu, um den Toleranzwert zu berechnen und anschließend stattdessen diese Methode aufzurufen.

    ```csharp
    private double ToleranceHelper(double expected)
    {
        return expected / 1000;
    }

    ...

    [TestMethod]
    public void RangeTest()
    {
        ...
        // old code
        // double tolerance = expected/1000;
        // new code
        double tolerance = ToleranceHelper(expected);
        Assert.AreEqual(expected, actual, tolerance);
    }
    ...
    ```

2. Wählen Sie **Alle ausführen** aus, um die umgestaltete Methode zu testen und zu überprüfen, dass Sie keinen Fehler eingeführt haben.

> [!NOTE]
> Wenn Sie einer Testklasse eine Hilfsmethode hinzufügen, die nicht im **Test-Explorer** angezeigt werden soll, fügen Sie der Methode nicht das <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>-Attribut hinzu.