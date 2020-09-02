---
title: 'Comment : modifier la langue de publication pour une application ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Publish language property
- ClickOnce deployment, changing publish language
- publishing, ClickOnce
ms.assetid: ef5024c4-cda1-4970-bc75-32a2a10c92c3
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 26e4074b731dad44cd9eed40f1c1cc755d786562
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683791"
---
# <a name="how-to-change-the-publish-language-for-a-clickonce-application"></a>Comment : modifier la langue de publication pour une application ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lors de la publication d’une [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application, l’interface utilisateur affichée lors de l’installation est définie par défaut sur la langue et la culture de votre ordinateur de développement. Si vous publiez une application localisée, vous devrez spécifier une langue et une culture correspondant à la version localisée. Cela est déterminé par la `Publish language` propriété de votre projet.  
  
 La `Publish language` propriété peut être définie dans la boîte de dialogue **options de publication** , accessible à partir de la page **publier** du **Concepteur de projets**.  
  
> [!NOTE]
> Les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles décrites dans l'Aide selon les paramètres actifs ou le mode d'édition. Pour modifier vos paramètres, choisissez **Paramètres d'importation et d'exportation** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-change-the-publish-language"></a>Pour modifier la langue de publication  
  
1. Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2. Cliquez sur l'onglet **Publier**.  
  
3. Cliquez sur le bouton **options** pour ouvrir la boîte de dialogue **options de publication** .  
  
4. Cliquez sur **Description**.  
  
5. Dans la boîte de dialogue **options de publication** , sélectionnez une langue et une culture dans la liste déroulante **langue de publication** , puis cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Publication d’applications ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Comment : publier une application ClickOnce à l'aide de l'Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
