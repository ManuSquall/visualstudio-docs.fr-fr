---
title: 'Procédure : spécifier l’emplacement à partir duquel les utilisateurs finaux vont installer | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], specifying an installation URL
- URLs, specifying an installation URL
- installation, specifying installation an URL
- Installation URL property
ms.assetid: 04a804bf-ed55-4a7a-a1e6-f63ed99c0276
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 82181d906adc3454dfe77ef4fb21d8bdf99df16f
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557987"
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>Comment : spécifier l'emplacement à partir duquel les utilisateurs finaux effectueront l'installation
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lors de la publication d’une application [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], l’emplacement où les utilisateurs accèdent au téléchargement et à l’installation de l’application n’est pas nécessairement l’emplacement où vous publiez initialement l’application. Par exemple, dans certaines organisations, un développeur peut publier une application sur un serveur intermédiaire, puis un administrateur déplace l’application vers un serveur Web.  
  
 Dans ce cas, vous pouvez utiliser la propriété `Installation URL` pour spécifier le serveur Web sur lequel les utilisateurs doivent accéder pour télécharger l’application. Cela est nécessaire pour que le manifeste d’application sache où rechercher les mises à jour.  
  
 La propriété `Installation URL` peut être définie sur la page **publier** du **Concepteur de projets**.  
  
 **Remarque** La propriété `Installation URL` peut également être définie à l’aide de **Assistant Publication**. Pour plus d’informations, consultez [Comment : publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-specify-an-installation-url"></a>Pour spécifier une URL d’installation  
  
1. Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2. Cliquez sur l’onglet **Publier**.  
  
3. Dans le champ URL d’installation, entrez l’emplacement d’installation à l’aide d’une URL complète au format `https://www.contoso.com/ApplicationName`ou d’un chemin d’accès UNC au format `\\Server\ApplicationName`.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour spécifier l’endroit où Visual Studio copie les fichiers](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [Publication d’applications ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Guide pratique pour publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
