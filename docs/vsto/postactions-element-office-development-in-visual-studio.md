---
title: "&lt;postActions&gt; élément (développement Office dans Visual Studio) | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <postActions> element
- postActions element
- <postActions> element
ms.assetid: 6e487549-fdd6-49bd-be7a-b91f1f964594
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 282a1bff821ee032d0d08038858c3a04fc7796ba
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ltpostactionsgt-element-office-development-in-visual-studio"></a>&lt;postActions&gt; élément (développement Office dans Visual Studio)
  L’élément `postActions` de l’espace de noms `vstav3` contient tous les éléments `postAction` qui décrivent des actions de post-déploiement, lesquelles s’exécutent après l’installation des solutions Office.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 L’élément `postActions` est facultatif et se trouve dans l’espace de noms `vstav3` . Un seul élément `postActions` est défini dans un manifeste de l’application.  
  
 L’élément `postActions` ne possède pas d’attributs.  
  
 `postActions` possède l’élément suivant.  
  
### <a name="postaction"></a>postAction  
 Facultatif. Le rôle de la `postAction` élément dans le `vstav3` espace de noms est défini dans [&#60; postAction &#62; Élément &#40; développement Office dans Visual Studio &#41; ](../vsto/postaction-element-office-development-in-visual-studio.md).  
  
## <a name="post-deployment-action-example"></a>Exemple d’action de post-déploiement  
  
### <a name="description"></a>Description  
 L’exemple de code suivant illustre l’élément `postActions` d’un manifeste de l’application pour une solution Office déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cet exemple de code fait partie d’un exemple plus complet fourni dans [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Code  
  
```  
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
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestes de déploiement pour les Solutions Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifeste d’application ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  