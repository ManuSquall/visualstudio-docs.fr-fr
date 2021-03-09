---
title: '&lt;&gt;élément vstoRuntime (développement Office dans Visual Studio)'
titleSuffix: ''
description: L’élément vstoRuntime de l’espace de noms vstav3 contient une version prise en charge de l’Visual Studio Tools pour Office Runtime pour une solution Office spécifique.
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <vstoRuntime> element
- <vstoRuntime> element
- vstoRuntime element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7c856836bd2ba107a2fa6c3017c5ecb2694fcf6b
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102468570"
---
# <a name="ltvstoruntimegt-element-office-development-in-visual-studio"></a>&lt;&gt;élément vstoRuntime (développement Office dans Visual Studio)
  L’élément `vstoRuntime` de l’espace de noms `vstav3` contient une version prise en charge du runtime Visual Studio Tools pour Office pour une solution Office spécifique.

## <a name="syntax"></a>Syntaxe

```xml
<vstoRuntime
    release
    version
    supportUrl />
```

## <a name="elements-and-attributes"></a>Éléments et attributs
 L’élément `vstoRuntime` est obligatoire et se trouve dans l’espace de noms `vstav3` . Si une solution Office prend en charge deux versions du runtime Visual Studio Tools pour Office, il existe deux éléments `vstoRuntime` dans le manifeste de l’application.

 L’élément `vstoRuntime` a les attributs suivants.

|Attribut|Description|
|---------------|-----------------|
|`release`|Obligatoire. Version mise en production du runtime de Visual Studio Tools pour Office.|
|`version`|Obligatoire. Numéro de version du runtime de Visual Studio Tools pour Office.|
|`supportUrl`|facultatif. Lien vers l’emplacement d’installation du runtime de Visual Studio Tools pour Office.|

 `vstoRuntime` ne comporte aucun élément.

## <a name="example"></a>Exemple
 L’exemple de code suivant illustre l’élément `vstoRuntime` d’un manifeste de l’application pour une solution Office déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cet exemple de code fait partie d’un exemple plus complet fourni dans [les manifestes d’application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).

```xml
<vstav3:vstoRuntime
    release="VSTOR40Beta1"
    version="10.0.20303"
    supportUrl="http://www.microsoft.com" />
```

## <a name="see-also"></a>Voir aussi

- [Manifestes d’application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifeste d’application ClickOnce](../deployment/clickonce-application-manifest.md)
