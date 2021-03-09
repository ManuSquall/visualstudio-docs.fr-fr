---
title: '&lt;&gt;élément postActions (développement Office)'
description: L’élément postActions de l’espace de noms vstav3 contient tous les éléments postAction qui décrivent les actions de postconnexion, qui s’exécutent après l’installation des solutions Office.
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <postActions> element
- postActions element
- <postActions> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5c4a66e270cd446996884262d380df0f7384f54f
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102470038"
---
# <a name="ltpostactionsgt-element-office-development"></a>&lt;&gt;élément postActions (développement Office)
  L’élément `postActions` de l’espace de noms `vstav3` contient tous les éléments `postAction` qui décrivent des actions de post-déploiement, lesquelles s’exécutent après l’installation des solutions Office.

## <a name="syntax"></a>Syntaxe

```xml
<postActions>
  <postAction>
    <entryPoint>
    </entryPoint>
    <postActionData>
    </postActionData>
  </postAction>
</postActions>
```

## <a name="elements-and-attributes"></a>Éléments et attributs
 L’élément `postActions` est facultatif et se trouve dans l’espace de noms `vstav3` . Un seul élément `postActions` est défini dans un manifeste d’application.

 L’élément `postActions` ne comporte pas d’attributs.

 `postActions` possède l’élément suivant.

### <a name="postaction"></a>postAction
 facultatif. Le rôle de l' `postAction` élément dans l' `vstav3` espace de noms est défini dans [&#60;élément postAction&#62; &#40;développement Office dans Visual Studio&#41;](../vsto/postaction-element-office-development-in-visual-studio.md).

## <a name="post-deployment-action-example"></a>Exemple d’action de postconnexion

### <a name="description"></a>Description
 L’exemple de code suivant illustre l’élément `postActions` d’un manifeste de l’application pour une solution Office déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cet exemple de code fait partie d’un exemple plus complet fourni dans [les manifestes d’application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Code

```xml
<vstav3:postActions>
  <vstav3:postAction>
    <vstav3:entryPoint
      class="PostDeploymentAction.PostDeploymentActionSample">
      <assemblyIdentity
        name="PostDeploymentAction"
        version="1.0.0.0"
        language="neutral"
        processorArchitecture="msil" />
    </vstav3:entryPoint>
    <vstav3:postActionData>
    </vstav3:postActionData>
  </vstav3:postAction>
</vstav3:postActions>
```

## <a name="see-also"></a>Voir aussi

- [Manifestes d’application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifeste d’application ClickOnce](../deployment/clickonce-application-manifest.md)
