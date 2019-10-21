---
title: 'Comment : configurer l’analyse du code pour une application Web ASP.NET | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.asp
ms.assetid: b3000b31-fd9d-489e-81a2-a4bee49453ba
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 423264362118343d573b417cd055d2d722df995e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657460"
---
# <a name="how-to-configure-code-analysis-for-an-aspnet-web-application"></a>Comment : configurer l'analyse du code pour une application Web ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] et [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)] vous pouvez sélectionner dans une liste d’ensembles de *règles* d’analyse du code à appliquer à [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] application Web. L’ensemble de règles par défaut est les règles recommandées par Microsoft Mininimum. Vous pouvez sélectionner un autre ensemble de règles à appliquer au site Web.

### <a name="to-configure-a-rule-set-for-an-aspnet-page-framework-project"></a>Pour configurer un ensemble de règles pour un projet d'infrastructure de page ASP.NET

1. Sélectionnez le site Web dans **Explorateur de solutions**.

2. Dans le menu **analyser** , cliquez sur **configurer l’analyse du code pour le site Web**.

3. Si vous avez sélectionné la solution et que la solution contient plusieurs projets, sélectionnez la configuration de build et le système d’exploitation cible dans les listes **configuration** et **plateforme** .

4. Pour chaque projet de la solution, cliquez sur la colonne **ensemble de règles** , puis cliquez sur le nom de l’ensemble de règles à exécuter.

5. Par défaut, l’analyse du code est exécutée sur tous les projets de la solution. Pour désactiver ou activer l’analyse du code pour un projet particulier, procédez comme suit :

    1. Cliquez avec le bouton droit sur le nom du projet, puis cliquez sur Propriétés.

    2. Activez ou désactivez la case à cocher **activer l’analyse du code** . Vous pouvez également exécuter l’analyse du code manuellement en sélectionnant **exécuter l’analyse du code sur le site Web** dans le menu **analyser** .

6. Dans la liste déroulante **exécuter cet ensemble de règles** , procédez comme suit :

    - Sélectionnez l’ensemble de règles que vous souhaitez utiliser.

    - Sélectionnez **\<Browse >** pour spécifier un ensemble de règles personnalisées existant qui ne figure pas dans la liste.

    - Définissez un ensemble de règles personnalisé. Pour plus d’informations, consultez [création d’ensembles de règles personnalisées](../code-quality/creating-custom-code-analysis-rule-sets.md).
