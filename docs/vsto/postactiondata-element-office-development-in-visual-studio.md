---
title: '&lt;postActionData&gt; élément (développement Office dans Visual Studio)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- <postActionData> element
- application manifests [Office development in Visual Studio], <postActionData> element
- postActionData element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9f96ecf7f7f6c0d465a9506edff41c4305d8d25e
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34692946"
---
# <a name="ltpostactiondatagt-element-office-development-in-visual-studio"></a>&lt;postActionData&gt; élément (développement Office dans Visual Studio)
  L’élément `postActionData` de l’espace de noms `vstav3` spécifie les données associées aux actions de post-déploiement qui s’exécutent après l’installation des solutions Office.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<postActionData>  
</postActionData>  
```  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 L’élément `postActionData` est facultatif et se trouve dans l’espace de noms `vstav3` . Il existe un élément `postActionData` défini dans un manifeste de l’application pour chaque action de post-déploiement.  
  
 L’élément `postActions` n’a pas d’attributs.  
  
 `postActions` n’a aucun élément enfant.  
  
## <a name="post-deployment-action-example"></a>Exemple d’action de post-déploiement  
  
### <a name="description"></a>Description  
 L’exemple de code suivant illustre l’élément `postAction` d’un manifeste de l’application pour une solution Office déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cet exemple de code fait partie d’un exemple plus complet fourni dans [manifestes d’Application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Code  
  
```xml  
<vstav3:postActionData>  
  data in any format  
</vstav3:postActionData>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Manifestes d’application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifeste d’application ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  