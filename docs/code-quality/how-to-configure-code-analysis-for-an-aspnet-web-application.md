---
title: 'Comment : configurer l’analyse du Code pour une Application Web ASP.NET dans Visual Studio'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.asp
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: bb1adaf9e97a950c6e9c53b3734debf5588fe0b9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
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