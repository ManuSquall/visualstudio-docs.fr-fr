---
title: "Migrer l’inscription de la classe débogueur 64 bits COM | Documents Microsoft"
ms.custom: 
ms.date: 11/10/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45cfcee6-7a68-4d4f-b3f6-e2d8a0fa066a
caps.latest.revision: 1
author: gregg-miskelly
ms.author: greggm
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: e273f31cb1f43ff79fd9a4ade37d112351dea9b5
ms.lasthandoff: 02/22/2017

---
# <a name="migrate-64-bit-debugger-com-class-registration"></a>Migrer le débogueur 64 bits d’inscription de classe COM

>**Remarque :** cette documentation est préliminaire et en fonction de la version de Visual Studio 2017 RC.

Pour les extensions de débogueur qui enregistrent des classes COM dans HKEY_CLASSES_ROOT (à l’aide de regsvr32, regasm ou écrire directement dans le Registre) et chargement msvsmon.exe (le débogueur distant), il est possible de fournir cette inscription à msvsmon sans avoir à écrire à HKEY_CLASSES_ROOT. Cela affecte les évaluateurs d’expression de débogueur .NET héritées ou les moteurs de débogage qui sont configurés pour se charger dans le processus de msvsmon.exe.

## <a name="msvsmon-comclass-def"></a>msvsmon comclass-définition

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

