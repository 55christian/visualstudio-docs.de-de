---
title: Aktualisieren von MDF-Dateien
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Express
- SQL Server LocalDB
- LocalDB
- SQLEXPRESS
- upgrading SQLExpress to SQLExpress
- upgrading to LocalDB
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 334898fe9bb6ec5a7dcd84e081f99994e18ccb89
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62565159"
---
# <a name="upgrade-mdf-files"></a>Aktualisieren von MDF-Dateien

In diesem Thema wird beschrieben, welche Optionen zum Aktualisieren einer Datenbankdatei (*mdf*) nach der Installation auf einer neueren Version von Visual Studio. Es enthält Anweisungen für die folgenden Aufgaben:

- Ein Upgrade für eine Datenbankdatei um eine neuere Version von SQL Server Express LocalDB zu verwenden.

- Ein Upgrade für eine Datenbankdatei um eine neuere Version von SQL Server Express verwenden

- Mit einer Datenbankdatei in Visual Studio arbeiten, aber behalten ihre Kompatibilität mit einer älteren Version von SQL Server Express oder LocalDB

- Stellen Sie die SQL Server Express die Standard-Datenbank-engine

Sie können Visual Studio verwenden, um ein Projekt zu öffnen, eine Datenbankdatei enthält (*mdf*), die mit einer älteren Version von SQL Server Express oder LocalDB erstellt wurde. Allerdings um weiterhin Ihr Projekt in Visual Studio entwickeln, benötigen Sie diese Version von SQL Server Express oder LocalDB, die auf dem gleichen Computer wie Visual Studio installiert, oder müssen Sie die Datenbankdatei aktualisieren. Wenn Sie die Datenbankdatei aktualisieren, wird nicht Sie darauf zugreifen, indem Sie ältere Versionen von SQL Server Express oder LocalDB verwenden können.

Sie können auch aufgefordert, eine Datei zu aktualisieren, die über eine frühere Version von SQL Server Express oder LocalDB erstellt wurde, wenn die Version der Datei nicht kompatibel mit der Instanz von SQL Server Express oder LocalDB, die derzeit installiert ist. Um das Problem zu beheben, fordert Visual Studio Sie auf die Datei zu aktualisieren.

> [!IMPORTANT]
> Es wird empfohlen, dass Sie die Datenbankdatei sichern, bevor Sie ein Upgrade durchführen.

> [!WARNING]
> Wenn Sie ein upgrade einer *mdf* Datei, die in LocalDB 2014 (V12) 32-Bit auf LocalDB 2016 von (V13) oder höher erstellt wurde, Sie ist nicht möglich, die Datei in der 32-Bit-Version von LocalDB erneut zu öffnen.

Vor dem upgrade einer Datenbank sollten Sie der folgenden Kriterien:

- Aktualisieren Sie nicht, wenn Sie auf das Projekt in einer älteren Version und eine neuere Version von Visual Studio arbeiten möchten.

- Aktualisieren Sie nicht, wenn Ihre Anwendung in Umgebungen verwendet werden, die SQL Server Express anstelle von LocalDB verwenden.

- Wenn Ihre Anwendung Remoteverbindungen verwendet nicht aktualisiert werden, da LocalDB nicht akzeptieren.

- Aktualisieren Sie nicht, wenn Ihre Anwendung auf Internet Information Services (IIS) basiert.

- Erwägen Sie ein Upgrade aus, wenn Sie datenbankanwendungen in einer sandboxumgebung testen möchten, aber nicht, eine Datenbank zu verwalten möchten.

### <a name="to-upgrade-a-database-file-to-use-the-localdb-version"></a>So aktualisieren eine Datenbankdatei aus, um die LocalDB-Version zu verwenden.

1. In **Server-Explorer**, wählen die **Herstellen einer Verbindung mit Datenbank** Schaltfläche.

2. In der **Verbindung hinzufügen** Dialogfeld geben die folgende Informationen:

    - **Datenquelle**: `Microsoft SQL Server (SqlClient)`

    - **Servername**:

        - Verwenden Sie die Standard-Version: `(localdb)\MSSQLLocalDB`.  Dies wird geben ProjectV12 oder ProjectV13, je nachdem, welche Version von Visual Studio installiert ist und wann die erste LocalDB-Instanz erstellt wurde. Die **MSSQLLocalDB** Knoten **Objekt-Explorer von SQL Server** zeigt, welche Version sie verweist auf.

        - Um eine bestimmte Version verwenden: `(localdb)\ProjectsV12` oder `(localdb)\ProjectsV13`, wobei V12 LocalDB 2014 ist und V13 LocalDB 2016.

    - **Anfügen einer Datenbankdatei**: Der physische Pfad der primären Datenbank *mdf* Datei.

    - **Der logische Name**: Der Name, die Sie mit der Datei verwenden möchten.

3. Klicken Sie auf die Schaltfläche **OK**.

4. Wenn Sie aufgefordert werden, wählen Sie die **Ja** Schaltfläche, um die Datei zu aktualisieren.

    Die Datenbank aktualisiert wird, wird der LocalDB-Datenbank-Engine angefügt und ist nicht mehr kompatibel mit einer älteren Version von LocalDB.

Sie können auch eine SQL Server Express-Verbindung, um LocalDB zu verwenden, indem Sie das Kontextmenü für die Verbindung öffnen, und wählen Sie dann ändern **Verbindung ändern**. In der **Verbindung ändern** Dialogfeld ändern den Namen des `(LocalDB)\MSSQLLocalDB`. In der **erweiterte Eigenschaften** Dialogfeld Feld, stellen Sie sicher, dass **Benutzerinstanz** nastaven NA hodnotu **"false"**.

### <a name="to-upgrade-a-database-file-to-use-the-sql-server-express-version"></a>So aktualisieren eine Datei zum Verwenden der SQL Server Express-version

1. Wählen Sie auf das Kontextmenü für die Verbindung mit der Datenbank, **Verbindung ändern**.

2. In der **Verbindung ändern** wählen Sie im Dialogfeld die **erweitert** Schaltfläche.

3. In der **erweiterte Eigenschaften** wählen Sie im Dialogfeld die **OK** klicken, ohne den Namen des Servers ändern.

    Die Datenbankdatei wird aktualisiert, entsprechend die aktuelle Version von SQL Server Express.

### <a name="to-work-with-the-database-in-visual-studio-but-retain-compatibility-with-sql-server-express"></a>Mit der Datenbank in Visual Studio arbeiten, aber behalten ihre Kompatibilität mit SQL Server Express

- Öffnen Sie in Visual Studio das Projekt, ohne dass eine Aktualisierung.

    - Wählen Sie zum Ausführen des Projekts die **F5** Schlüssel.

    - Öffnen Sie zum Bearbeiten der Datenbank die *mdf* Datei **Projektmappen-Explorer**, und erweitern Sie im Knoten **Server-Explorer** zum Arbeiten mit Ihrer Datenbank.

### <a name="to-make-sql-server-express-the-default-database-engine"></a>Um SQL Server Express, die Standard-Datenbank-Engine zu machen.

1. Wählen Sie auf der Menüleiste **Tools** > **Optionen**.

2. In der **Optionen** Dialogfeld erweitern Sie die **Datenbanktools** Optionen, und wählen Sie dann **Datenverbindungen**.

3. In der **SQL Server-Instanzname** Text geben den Namen der Instanz von SQL Server Express oder LocalDB, die Sie verwenden möchten. Wenn die Instanz die Bezeichnung nicht ist, geben Sie `.\SQLEXPRESS or (LocalDB)\MSSQLLocalDB`.

4. Klicken Sie auf die Schaltfläche **OK**.

    SQL Server Express werden die Standard-Datenbank-Engine für Ihre Anwendungen.

## <a name="see-also"></a>Siehe auch

- [Zugreifen auf Daten in Visual Studio](accessing-data-in-visual-studio.md)