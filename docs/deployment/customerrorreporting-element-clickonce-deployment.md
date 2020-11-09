---
title: '&lt;&gt;élément customErrorReporting (déploiement ClickOnce) | Microsoft Docs'
description: L’élément customErrorReporting spécifie un URI à afficher lorsqu’une erreur se produit au lieu d’une boîte de dialogue d’erreur affichant la pile d’exception.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <customErrorReporting> element [ClickOnce deployment manifest]
ms.assetid: 7d31816e-c692-46b5-9cc9-753284b3bcda
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5576912fb428e15a6f8164e52d558e255e184fe3
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2020
ms.locfileid: "94382518"
---
# <a name="ltcustomerrorreportinggt-element-clickonce-deployment"></a>&lt;&gt;élément customErrorReporting (déploiement ClickOnce)
Spécifie un URI à afficher en cas d'erreur.

## <a name="syntax"></a>Syntaxe

```xml
<customErrorReporting
   uri
/>
```

## <a name="remarks"></a>Notes
 Cet élément est facultatif. Sans lui, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] affiche une boîte de dialogue d’erreur indiquant la pile d’exception. Si l' `customErrorReporting` élément est présent, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] affichera à la place l’URI indiqué par le `uri` paramètre. L’URI cible inclura la classe d’exception externe, la classe d’exception interne et le message d’exception interne en tant que paramètres.

 Utilisez cet élément pour ajouter la fonctionnalité de création de rapports d’erreurs à votre application. Étant donné que l’URI généré contient des informations sur le type d’erreur, votre site Web peut analyser ces informations et afficher, par exemple, un écran de dépannage approprié.

## <a name="example"></a>Exemple
 L’extrait de code suivant montre l' `customErrorReporting` élément, ainsi que l’URI généré qu’il peut produire.

```xml
<customErrorReporting uri=http://www.contoso.com/applications/error.asp />

Example Generated Error:
http://www.contoso.com/applications/error.asp? outer=System.Deployment.Application.InvalidDeploymentException&&inner=System.Deployment.Application.InvalidDeploymentException&&msg=The%20application%20manifest%20is%20signed,%20but%20the%20deployment%20manifest%20is%20unsigned.%20Both%20manifests%20must%20be%20either%20signed%20or%20unsigned.
```

## <a name="see-also"></a>Voir aussi
- [Manifeste de déploiement ClickOnce](../deployment/clickonce-deployment-manifest.md)