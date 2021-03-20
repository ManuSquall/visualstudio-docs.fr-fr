---
title: require-mssql
description: l’outil devinit requiert-MSSQL.
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: e39a03fe70d2e4399b758e06e9acb2e0de59ef08
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672520"
---
# <a name="require-mssql"></a>require-mssql

> [!IMPORTANT]
> Depuis le 12 avril 2021, la connexion à GitHub Codespaces à partir de Visual Studio 2019 ne sera plus prise en charge et cette version préliminaire privée s’est terminée. Nous nous concentrons sur les expériences en constante évolution d’une boucle interne basée sur le Cloud et de solutions VDI optimisées pour un large éventail de charges de travail Visual Studio. Dans le cadre de cet article `devinit` , les outils associés ne seront plus disponibles. Nous vous encourageons à participer au Forum de la communauté des développeurs pour Visual Studio afin d’obtenir des informations sur les futures versions préliminaires et les informations de feuille de route.

L' `require-mssql` outil est utilisé pour installer [Microsoft SQL Server édition développeur 2019](https://www.microsoft.com/sql-server/application-development) à partir de l’aide de l’ISO de MS SQL Server. SQL Server sera disponible sur `localhost` l’authentification Windows intégrée. SQL Server sera accessible avec la chaîne de connexion `"Server=localhost;Integrated Security=true;"` .

## <a name="usage"></a>Utilisation

Si les `input` Propriétés et `additionalOptions` sont omises ou vides, l’outil suivra le comportement [par défaut](#default-behavior) détaillé ci-dessous.

| Nom                                             | Type   | Obligatoire | Valeur                                                                                   |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------------------------|
| **commentaires**                                     | string | Non       | Propriété de commentaires facultative. Non utilisé.                                                   |
| [**entrée**](#input)                              | string | Non       | Pour plus d’informations, consultez l' [entrée](#input) ci-dessous.                                                  |
| [**additionalOptions**](#additional-options)     | string | Non       | Non utilisé. Pour plus d’informations, consultez les [options supplémentaires](#additional-options) ci-dessous.              |

### <a name="input"></a>Entrée

La `input` propriété peut être une chaîne avec l’une des deux valeurs suivantes :

| Value     | Description                              |
|-----------|------------------------------------------|
| installer   | Installe SQL Server.                     |
| uninstall | Désinstalle toutes les installations de SQL Server. |

### <a name="additional-options"></a>Options supplémentaires

Non utilisé.

### <a name="default-behavior"></a>Comportement par défaut

Le comportement par défaut de l' `require-mssql` outil consiste à installer SQL Server.

### <a name="built-in-options"></a>Options intégrées

L' `require-mssql` outil définit un certain nombre d’arguments de ligne de commande du programme d’installation pour s’assurer que le programme d’installation peut s’exécuter sans écran. Ces arguments sont répertoriés ci-dessous et leur documentation est disponible dans la [documentation d’installation de SQL](/sql/database-engine/install-windows/install-sql-server-from-the-command-prompt?view=sql-server-ver15&preserve-view=true).

| Nom                                                               | Description |
|--------------------------------------------------------------------|-------------|
| /q                                                                 |             |
| /ACTION = installation                                                    |             |
| /FEATURES = SQLEngine, base de données locale                                       |             |
| /UpdateEnabled                                                     |             |
| /UpdateSource = MU                                                   |             |
| /X86 = false                                                         |             |
| /INSTANCENAME = MSSQLSERVER                                          |             |
| /INSTALLSHAREDDIR = "C:\Program Files\Microsoft SQL Server"          |             |
| /INSTALLSHAREDWOWDIR = "C:\Program Files (x86) \Microsoft SQL Server" |             |
| /SQLSVCINSTANTFILEINIT = true                                        |             |
| /INSTANCEDIR = "C:\Program Files\Microsoft SQL Server"               |             |
| /AGTSVCACCOUNT = "NT Service\SQLSERVERAGENT"                         |             |
| /AGTSVCSTARTUPTYPE = manuel                                          |             |
| /SQLSVCSTARTUPTYPE = automatique                                       |             |
| /SQLCOLLATION = "SQL_Latin1_General_CP1_CI_AS"                       |             |
| /SQLSVCACCOUNT = "NT Service\MSSQLSERVER"                            |             |
| /SQLSYSADMINACCOUNTS = administrateurs                                |             |
| /IACCEPTSQLSERVERLICENSETERMS                                      |             |

## <a name="example-usage"></a>Exemple d’utilisation
Vous trouverez ci-dessous un exemple de la façon d’exécuter `require-msssql` à l’aide d’un `.devinit.json` .

#### <a name="devinitjson-that-will-install-mssql"></a>.devinit.jssur qui installe MSSQL :
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-mssql",
            "input": "install",
        }
    ]
}
```