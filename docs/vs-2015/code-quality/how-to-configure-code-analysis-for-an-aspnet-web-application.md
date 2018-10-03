---
title: 'Comment : configurer l’analyse du Code pour une Application Web ASP.NET | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.codeanalysis.propertypages.asp
ms.assetid: b3000b31-fd9d-489e-81a2-a4bee49453ba
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 9b611e303c61e7be9586d6d746e5c859c8dbb5b9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47501577"
---
# <a name="how-to-configure-code-analysis-for-an-aspnet-web-application"></a>Comment : configurer l'analyse du code pour une application Web ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Comment : configurer l’analyse du Code pour une Application Web ASP.NET](https://docs.microsoft.com/visualstudio/code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application).  
  
Dans [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] et [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)] vous pouvez sélectionner dans une liste de l’analyse du Code *ensembles de règles* à appliquer à [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] application Web. L’ensemble de règles par défaut est la règles recommandées de Microsoft intitule. Vous pouvez sélectionner un autre ensemble de règles à appliquer au site Web.  
  
### <a name="to-configure-a-rule-set-for-an-aspnet-page-framework-project"></a>Pour configurer un ensemble de règles pour un projet d'infrastructure de page ASP.NET  
  
1.  Sélectionnez le site Web dans **l’Explorateur de solutions**.  
  
2.  Sur le **analyser** menu, cliquez sur **configurer l’analyse du Code pour le Site Web**.  
  
3.  Si vous avez sélectionné la solution et la solution comporte plusieurs projets, sélectionnez le build cible et configuration de système d’exploitation le **Configuration** et **plateforme** répertorie.  
  
4.  Pour chaque projet dans la solution, cliquez sur le **l’ensemble de règles** colonne, puis cliquez sur le nom de la règle de configuration pour exécuter.  
  
5.  Par défaut, l’analyse du code est exécutée sur tous les projets dans la solution. Pour désactiver ou activer l’analyse du code pour un projet particulier, procédez comme suit :  
  
    1.  Cliquez sur le nom de projet, puis sur Propriétés.  
  
    2.  Cochez ou décochez la **Enable Code Analysis** case à cocher. Vous pouvez également exécuter l’analyse du code manuellement en sélectionnant **exécuter l’analyse du Code sur le Site Web** à partir de la **analyser** menu.  
  
6.  Dans le **exécuter cet ensemble de règles** déroulante liste, procédez comme suit :  
  
    -   Sélectionnez l’ensemble de règles que vous souhaitez utiliser.  
  
    -   Sélectionnez  **\<Parcourir >** pour spécifier une règle personnalisée existante définie qui n’est pas dans la liste.  
  
    -   Définissez un ensemble de règles personnalisé. Pour plus d’informations, consultez [création d’ensembles de règles personnalisés](../code-quality/creating-custom-code-analysis-rule-sets.md).



