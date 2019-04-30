---
title: '&lt;postAction&gt; élément (développement Office dans Visual Studio)'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <postAction> element
- <postAction> element
- postAction element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 53cf47ef9a78ebb54c377e19b4f7fbad444bbfcd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62976533"
---
# <a name="ltpostactiongt-element-office-development-in-visual-studio"></a>&lt;postAction&gt; élément (développement Office dans Visual Studio)
  L’élément `postAction` de l’espace de noms `vstav3` contient les éléments `entrypoint` et tous les éléments `postActionData` associés à des actions de post-déploiement, lesquelles s’exécutent après l’installation des solutions Office.

## <a name="syntax"></a>Syntaxe

```xml
<postAction>
  <entryPoint>
  </entryPoint>
  <postActionData>
  </postActionData>
</postAction>
```

## <a name="elements-and-attributes"></a>Éléments et attributs
 L’élément `postAction` est facultatif et se trouve dans l’espace de noms `vstav3` . Il existe un seul élément `postAction` défini dans un manifeste de l’application pour chaque action de post-déploiement.

 L’élément `postAction` ne comporte pas d’attributs.

 `postAction` comporte les éléments suivants.

### <a name="entrypoint"></a>entrypoint
 Optionnel. Le rôle de la `entryPoint` élément dans le `vstav3` espace de noms est défini dans [ &#60;entryPoints&#62; élément &#40;développement Office dans Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md).

### <a name="postactiondata"></a>postActionData
 Optionnel. Le rôle de la `postActionData` élément dans le `vstav3` espace de noms est défini dans [ &#60;postActionData&#62; élément &#40;développement Office dans Visual Studio&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md).

## <a name="post-deployment-action-example"></a>Exemple d’action de post-déploiement

### <a name="description"></a>Description
 L’exemple de code suivant illustre l’élément `postAction` d’un manifeste de l’application pour une solution Office déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cet exemple de code fait partie d’un exemple plus complet fourni dans [manifestes d’Application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Code

```xml
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
```

## <a name="see-also"></a>Voir aussi

- [Manifestes d’application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifeste d’application ClickOnce](../deployment/clickonce-application-manifest.md)
