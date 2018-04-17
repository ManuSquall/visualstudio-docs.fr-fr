---
title: '&lt;vstoRuntime&gt; élément (développement Office dans Visual Studio) | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <vstoRuntime> element
- <vstoRuntime> element
- vstoRuntime element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ee2d50d69c363d5073a09b953c00d22a11ef5315
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ltvstoruntimegt-element-office-development-in-visual-studio"></a>&lt;vstoRuntime&gt; élément (développement Office dans Visual Studio)
  L’élément `vstoRuntime` de l’espace de noms `vstav3` contient une version prise en charge du runtime Visual Studio Tools pour Office pour une solution Office spécifique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|`supportUrl`|Facultatif. Lien vers l’emplacement d’installation du runtime de Visual Studio Tools pour Office.|  
  
 `vstoRuntime` ne comporte aucun élément.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant illustre l’élément `vstoRuntime` d’un manifeste de l’application pour une solution Office déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cet exemple de code fait partie d’un exemple plus complet fourni dans [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
```  
<vstav3:vstoRuntime  
    release="VSTOR40Beta1"  
    version="10.0.20303"  
    supportUrl="http://www.microsoft.com" />  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestes de déploiement pour les Solutions Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifeste d’application ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  