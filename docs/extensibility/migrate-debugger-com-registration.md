---
title: Migrer l’inscription de classe COM du débogueur 64 bits | Microsoft Docs
description: Découvrez comment inscrire des classes COM sur msvsmon pour les extensions de débogueur sans écrire dans HKEY_CLASSES_ROOT.
ms.custom: SEO-VS-2020
ms.date: 11/10/2016
ms.topic: conceptual
ms.assetid: 45cfcee6-7a68-4d4f-b3f6-e2d8a0fa066a
author: gregg-miskelly
ms.author: greggm
manager: jmartens
ms.workload:
- greggm
ms.openlocfilehash: adc1db57de2167ff3caa0e87e1075c8ff5b462e4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886715"
---
# <a name="migrate-64-bit-debugger-com-class-registration"></a>Migrer l’inscription de classe COM du débogueur 64 bits

Pour les extensions de débogueur qui inscrivent des classes COM dans HKEY_CLASSES_ROOT en utilisant regasm, regsvr32 ou en écrivant directement dans le registre et chargées dans *msvsmon.exe* (le débogueur distant), il est maintenant possible de fournir cet enregistrement à msvsmon sans avoir à écrire dans HKEY_CLASSES_ROOT. Cela affecte les évaluateurs d’expressions de débogueur .NET hérités ou les moteurs de débogage qui sont configurés pour être chargés dans le processus de *msvsmon.exe* .

## <a name="msvsmon-comclass-def"></a>msvsmon-ComClass-def

Pour utiliser cette technique, ajoutez un **.msvsmon-comclass-def.jssur le* fichier en regard de msvsmon (INSTALLDIR :* \Common7\IDE\Remote Debugger\x64 *).

Voici un exemple de fichier msvsmon-ComClass-def qui inscrit une classe managée et une classe Native :

Nom du fichier : *MyCompany.MyExample.msvsmon-comclass-def.js*

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
