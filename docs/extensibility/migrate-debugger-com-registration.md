---
title: Migrer l’inscription de classe Windows 64 bits débogueur COM | Documents Microsoft
ms.custom: ''
ms.date: 11/10/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 45cfcee6-7a68-4d4f-b3f6-e2d8a0fa066a
author: gregg-miskelly
ms.author: greggm
manager: douge
ms.workload:
- greggm
ms.openlocfilehash: 28516038170dd34028d11bf9a070cf265ecfd830
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="migrate-64-bit-debugger-com-class-registration"></a>Migrer le débogueur 64 bits d’inscription de classe COM

Pour les extensions de débogueur qui enregistrent des classes COM dans HKEY_CLASSES_ROOT (à l’aide de regsvr32, regasm, ou directement l’écriture dans le Registre) et chargement dans msvsmon.exe (le débogueur distant), il est possible de fournir cette inscription à msvsmon sans avoir besoin de pour écrire dans HKEY_CLASSES_ROOT. Cela affecte les évaluateurs d’expression de débogueur .NET héritées ou les moteurs de débogage qui sont configurés pour se charger dans le processus msvsmon.exe.

## <a name="msvsmon-comclass-def"></a>msvsmon-comclass-def.

Pour utiliser cette technique, ajoutez un fichier de *.msvsmon-comclass-def.json en regard de msvsmon (InstallDir:\Common7\IDE\Remote Debugger\x64).

Voici un exemple de fichier msvsmon-comclass-def qui enregistre une gérés et une classe native :

Nom de fichier : MyCompany.MyExample.msvsmon-comclass-def.json

```json
{
  "managedCOMClasses": [
    {
      "clsid": "{C9F48B25-36ED-4B22-8210-98BC5BE4D1E7}",
      "assemblyName": "MyCompany.MyAssembly",
      "className": "MyCompany.MyNamespace.MyClass"
    }
  ],
  "nativeCOMClasses": [
    {
      "clsid": "{42A476E9-8FA7-44D5-ADFE-216AD371EEC9}",
      "dllPath": "MyExample.dll"
    }
  ]
}
```
