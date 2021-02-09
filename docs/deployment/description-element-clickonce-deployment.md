---
title: '&lt;description &gt; , élément (déploiement ClickOnce) | Microsoft Docs'
description: L’élément Description identifie les informations sur l’application utilisées pour créer une présence de Shell et un élément Ajout/suppression de programmes dans le panneau de configuration.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#description
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <description> element [ClickOnce deployment manifest]
ms.assetid: 18f6919e-a3ab-4942-a57d-167fabfac44e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8dee33fca027ce47ede8315f7956479ee2394382
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893085"
---
# <a name="ltdescriptiongt-element-clickonce-deployment"></a>&lt;description &gt; , élément (déploiement ClickOnce)
Identifie les informations de l’application utilisées pour créer une présence de Shell et un élément **Ajouter ou supprimer des programmes** dans le panneau de configuration.

## <a name="syntax"></a>Syntaxe

```xml

      <description 
   publisher 
   product
   suiteName
   supportUrl
/>
```

## <a name="elements-and-attributes"></a>Éléments et attributs
 L’élément `description` est obligatoire et se trouve dans l’espace de noms `urn:schemas-microsoft-com:asm.v1` . Il ne contient pas d’éléments enfants et a les attributs suivants.

|Attribut|Description|
|---------------|-----------------|
|`publisher`|Obligatoire. Identifie le nom de la société utilisé pour l’emplacement des icônes dans le menu **Démarrer** de Windows et l’élément **Ajout/suppression de programmes** dans le panneau de configuration, lorsque le déploiement est configuré pour l’installation.|
|`product`|Obligatoire. Identifie le nom complet du produit. Utilisé comme titre de l’icône installée dans le menu **Démarrer** de Windows.|
|`suiteName`|Facultatif. Identifie un sous-dossier dans le `publisher` dossier du menu **Démarrer** de Windows.|
|`supportUrl`|Facultatif. Spécifie une URL de support technique qui est affichée dans l’élément **Ajout/suppression de programmes** du panneau de configuration. Un raccourci vers cette URL est également créé pour la prise en charge des applications dans le menu **Démarrer** de Windows, lorsque le déploiement est configuré pour l’installation.|

## <a name="remarks"></a>Remarques
 L’élément description est requis dans toutes les configurations de déploiement.

## <a name="example"></a>Exemple
 L’exemple de code suivant illustre un `description` élément dans un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifeste de déploiement. Cet exemple de code fait partie d’un exemple plus complet fourni pour la rubrique du [manifeste de déploiement ClickOnce](../deployment/clickonce-deployment-manifest.md) .

```xml
<description
  asmv2:publisher="My Company Name"
  asmv2:product="My Application"
  xmlns="urn:schemas-microsoft-com:asm.v1" />
```

## <a name="see-also"></a>Voir aussi
- [Manifeste de déploiement ClickOnce](../deployment/clickonce-deployment-manifest.md)