---
title: '&lt;Description&gt; , élément (déploiement ClickOnce) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#description
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <description> element [ClickOnce deployment manifest]
ms.assetid: 18f6919e-a3ab-4942-a57d-167fabfac44e
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 473ebf814ab65c34ee99cab0cf2cc239e0d013eb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47493054"
---
# <a name="ltdescriptiongt-element-clickonce-deployment"></a>&lt;Description&gt; , élément (déploiement ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [ &lt;description&gt; , élément (déploiement ClickOnce)](https://docs.microsoft.com/visualstudio/deployment/description-element-clickonce-deployment).  
  
Identifie les informations de l’application utilisées pour créer la présence d’un shell et un **Ajout / Suppression de programmes** élément dans le panneau de configuration.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      <description   
   publisher   
   product  
   suiteName  
   supportUrl  
/>  
```  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 L’élément `description` est obligatoire et se trouve dans l’espace de noms `urn:schemas-microsoft-com:asm.v1`. Il ne contient aucun élément enfant et a les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`publisher`|Obligatoire. Identifie le nom de société utilisé pour la sélection élective d’icône dans le Windows **Démarrer** menu et le **Ajout / Suppression de programmes** élément dans le panneau de configuration, lorsque le déploiement est configuré pour l’installation.|  
|`product`|Obligatoire. Identifie le nom de produit complet. Utilisé en tant que le titre de l’icône installée dans le Windows **Démarrer** menu.|  
|`suiteName`|Facultatif. Identifie un sous-dossier dans le `publisher` dossier dans le Windows **Démarrer** menu.|  
|`supportUrl`|Facultatif. Spécifie une URL de prise en charge qui est indiquée dans le **Ajout / Suppression de programmes** élément dans le panneau de configuration. Un raccourci vers cette URL est également créé pour la prise en charge de l’application dans le Windows **Démarrer** menu, lorsque le déploiement est configuré pour l’installation.|  
  
## <a name="remarks"></a>Notes  
 L’élément description est requis dans toutes les configurations de déploiement.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant illustre un `description` élément dans un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifeste de déploiement. Cet exemple de code fait partie d’un exemple plus complet fourni pour le [du manifeste de déploiement ClickOnce](../deployment/clickonce-deployment-manifest.md) rubrique.  
  
```  
<description   
  asmv2:publisher="My Company Name"  
  asmv2:product="My Application"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Manifeste de déploiement ClickOnce](../deployment/clickonce-deployment-manifest.md)



