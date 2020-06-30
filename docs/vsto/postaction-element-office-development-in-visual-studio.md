---
title: '&lt;&gt;élément postAction (développement Office dans Visual Studio)'
ms.date: 02/02/2017
ms.topic: reference
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
ms.openlocfilehash: 149aa0cf8543f5b5b1b5ada18a8b2f0e58f063d0
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546937"
---
# <a name="ltpostactiongt-element-office-development-in-visual-studio"></a>&lt;&gt;élément postAction (développement Office dans Visual Studio)
  L’élément `postAction` de l’espace de noms `vstav3` contient les éléments `entrypoint` et tous les éléments `postActionData` associés à des actions de post-déploiement, lesquelles s’exécutent après l’installation des solutions Office.

## <a name="syntax"></a>Syntax

```xml
<postAction>
  <entryPoint>
  </entryPoint>
  <postActionData>
  </postActionData>
</postAction>
```

## <a name="elements-and-attributes"></a>Éléments et attributs
 L’élément `postAction` est facultatif et se trouve dans l’espace de noms `vstav3` . Il existe un élément `postAction` défini dans un manifeste de l’application pour chaque action de post-déploiement.

 L’élément `postAction` ne comporte pas d’attributs.

 `postAction` comporte les éléments suivants.

### <a name="entrypoint"></a>entryPoint
 facultatif. Le rôle de l' `entryPoint` élément dans l' `vstav3` espace de noms est défini dans [&#60;élément entryPoints&#62; &#40;développement Office dans Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md).

### <a name="postactiondata"></a>postActionData
 facultatif. Le rôle de l' `postActionData` élément dans l' `vstav3` espace de noms est défini dans [&#60;élément postActionData&#62; &#40;développement Office dans Visual Studio&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md).

## <a name="post-deployment-action-example"></a>Exemple d’action de postconnexion

### <a name="description"></a>Description
 L’exemple de code suivant illustre l’élément `postAction` d’un manifeste de l’application pour une solution Office déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cet exemple de code fait partie d’un exemple plus complet fourni dans [les manifestes d’application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).

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
