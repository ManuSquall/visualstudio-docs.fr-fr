---
title: '&lt;Description&gt; élément (déploiement ClickOnce) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#description
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <description> element [ClickOnce deployment manifest]
ms.assetid: 18f6919e-a3ab-4942-a57d-167fabfac44e
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 4701bc77350d080ef9ad9c1eb56b80c344b0ff0a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ltdescriptiongt-element-clickonce-deployment"></a>&lt;Description&gt; élément (déploiement ClickOnce)
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
 L’élément `description` est obligatoire et se trouve dans l’espace de noms `urn:schemas-microsoft-com:asm.v1`. Il ne contienne aucun élément enfant et possède les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`publisher`|Obligatoire. Identifie le nom de société utilisé pour la sélection élective de l’icône dans les fenêtres **Démarrer** menu et **Ajout / Suppression de programmes** élément dans le panneau de configuration, lorsque le déploiement est configuré pour l’installation.|  
|`product`|Obligatoire. Identifie le nom complet du produit. Utilisé comme titre de l’icône installée dans les fenêtres **Démarrer** menu.|  
|`suiteName`|Facultatif. Identifie un sous-dossier dans le `publisher` dossier dans les fenêtres **Démarrer** menu.|  
|`supportUrl`|Facultatif. Spécifie une URL de prise en charge qui est indiquée dans le **Ajout / Suppression de programmes** élément dans le panneau de configuration. Un raccourci vers cette URL est également créé pour la prise en charge de l’application dans les fenêtres **Démarrer** menu, lorsque le déploiement est configuré pour l’installation.|  
  
## <a name="remarks"></a>Notes  
 L’élément description est requis dans toutes les configurations de déploiement.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant illustre un `description` élément dans un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifeste de déploiement. Cet exemple de code fait partie d’un exemple plus complet fourni pour le [le manifeste de déploiement ClickOnce](../deployment/clickonce-deployment-manifest.md) rubrique.  
  
```  
<description   
  asmv2:publisher="My Company Name"  
  asmv2:product="My Application"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Manifeste de déploiement ClickOnce](../deployment/clickonce-deployment-manifest.md)