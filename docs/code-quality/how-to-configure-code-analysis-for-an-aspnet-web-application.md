---
title: 'Comment : configurer l’analyse du Code pour une Application Web ASP.NET dans Visual Studio | Documents Microsoft'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.asp
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 6f0868c825c4e3632a882a044b69e676053800ea
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-configure-code-analysis-for-an-aspnet-web-application"></a>Comment : configurer l'analyse du code pour une application Web ASP.NET

Dans Visual Studio, vous pouvez sélectionner dans une liste d’analyse du Code *ensembles de règles* à appliquer au [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] application Web. L’ensemble de règles par défaut est de règles Microsoft minimales recommandées. Vous pouvez sélectionner un autre ensemble de règles à appliquer au site Web.

1. Sélectionnez le site Web dans **l’Explorateur de solutions**.

2. Sur le **analyser** menu, cliquez sur **configurer l’analyse du Code pour le Site Web**.

3. Si vous avez sélectionné la solution et la solution comporte plusieurs projets, sélectionnez le build cible et configuration de système d’exploitation le **Configuration** et **plateforme** répertorie.

4. Pour chaque projet dans la solution, cliquez sur le **l’ensemble de règles** colonne, puis cliquez sur le nom de la règle est configuré pour s’exécuter.

5. Par défaut, l’analyse du code est exécutée sur tous les projets dans la solution. Pour désactiver ou activer l’analyse du code pour un projet particulier, procédez comme suit :

    1. Cliquez sur le nom du projet, puis sur Propriétés.

    2. Activez ou désactivez le **activer l’analyse du Code** case à cocher. Vous pouvez également exécuter l’analyse du code manuellement en sélectionnant **exécuter l’analyse du Code sur le Site Web** à partir de la **analyser** menu.

6. Dans le **exécuter cet ensemble de règles** déroulante liste, procédez comme suit :

    - Sélectionnez l’ensemble de règles que vous souhaitez utiliser.

    - Sélectionnez  **\<Parcourir >** pour spécifier une règle personnalisée existante du jeu qui n’est pas dans la liste.

    - Définir un [ensemble de règles personnalisé](../code-quality/how-to-create-a-custom-rule-set.md).