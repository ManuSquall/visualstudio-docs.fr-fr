---
title: 'Comment : spécifier l’emplacement où les utilisateurs finaux installent à partir | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6b0731a5e218b6fcd6a13ac00fe19daad86f6b3d
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39078083"
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>Comment : spécifier l’emplacement où les utilisateurs finaux installent à partir
Lorsque vous publiez un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application, l’emplacement où les utilisateurs à télécharger et installer l’application n’est pas nécessairement l’emplacement où vous avez initialement publié l’application. Par exemple, dans certaines organisations, un développeur peut publier une application sur un serveur intermédiaire, puis un administrateur peut la déplacer vers un serveur Web.  
  
 Dans ce cas, vous pouvez utiliser le `Installation URL` propriété pour spécifier le serveur Web où les utilisateurs devront accéder pour télécharger l’application. Cela est nécessaire pour que le manifeste d’application sache où rechercher les mises à jour.  
  
 Le `Installation URL` propriété peut être définie sur le **publier** page de la **Concepteur de projet**.  
  
 **Remarque** le `Installation URL` propriété peut également être définie à l’aide de la **Assistant Publication**. Pour plus d’informations, consultez [Comment : publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-specify-an-installation-url"></a>Pour spécifier une URL d’Installation  
  
1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2.  Cliquez sur le **publier** onglet.  
  
3.  Dans le champ URL de l’Installation, entrez l’emplacement d’installation à l’aide d’une URL qualifiée complète en utilisant le format *http://www.microsoft.com/ApplicationName*, ou un chemin d’accès UNC au format  *\\\Server\ApplicationName*.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : spécifier l’endroit où Visual Studio copie les fichiers](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [Publication d’applications ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Comment : publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)