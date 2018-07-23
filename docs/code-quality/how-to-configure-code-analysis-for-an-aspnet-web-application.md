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
ms.openlocfilehash: c924a866f1bb34f41664fbf62e372b77f4d2620e
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2018
ms.locfileid: "39178235"
---
# <a name="how-to-configure-code-analysis-for-an-aspnet-web-application"></a>Comment : configurer l'analyse du code pour une application Web ASP.NET

Dans Visual Studio, vous pouvez sélectionner dans une liste de l’analyse du Code *ensembles de règles* à appliquer à [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] application web. L’ensemble de règles par défaut est de règles Microsoft minimales recommandées. Vous pouvez sélectionner un autre ensemble de règles à appliquer au site web.

1. Sélectionnez le site web dans **l’Explorateur de solutions**.

2. Sur le **analyser** menu, cliquez sur **configurer l’analyse du Code pour le Site Web**.

3. Si vous avez sélectionné la solution et la solution comporte plusieurs projets, sélectionnez le build cible et configuration de système d’exploitation le **Configuration** et **plateforme** répertorie.

4. Pour chaque projet dans la solution, cliquez sur le **l’ensemble de règles** colonne, puis cliquez sur le nom de la règle de configuration pour exécuter.

5. Par défaut, l’analyse du code est exécutée sur tous les projets dans la solution. Pour désactiver ou activer l’analyse du code pour un projet particulier, procédez comme suit :

    1. Cliquez sur le nom de projet, puis sur Propriétés.

    2. Cochez ou décochez la **Enable Code Analysis** case à cocher. Vous pouvez également exécuter l’analyse du code manuellement en sélectionnant **exécuter l’analyse du Code sur le Site Web** à partir de la **analyser** menu.

6. Dans le **exécuter cet ensemble de règles** déroulante liste, procédez comme suit :

    - Sélectionnez l’ensemble de règles que vous souhaitez utiliser.

    - Sélectionnez  **\<Parcourir >** pour spécifier une règle personnalisée existante définie qui n’est pas dans la liste.

    - Définir un [ensemble de règles personnalisé](../code-quality/how-to-create-a-custom-rule-set.md).