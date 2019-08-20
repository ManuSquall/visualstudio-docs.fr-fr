---
title: 'Procédure : Synchroniser des ensembles de règles de projet de Code avec la stratégie d’archivage du projet d’équipe | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.selecttfsruleset
ms.assetid: 9b02f934-2db6-41ec-aaff-9c31ceec2f04
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 32558f746745fdcb717aa7c218f996924418ae79
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201304"
---
# <a name="how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy"></a>Procédure : Synchroniser des ensembles de règles applicables à des projets de code avec la stratégie d'archivage du projet d'équipe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous synchronisez les paramètres d’analyse de code pour les projets de code à la stratégie d’archivage du projet d’équipe en spécifiant un ensemble de règles qui contient au moins les règles qui sont spécifiés dans l’ensemble de règles pour la stratégie d’archivage. Votre développeur en chef peut informer vous du nom et l’emplacement de l’ensemble de règles pour la stratégie d’archivage. Vous pouvez utiliser une des options suivantes pour vous assurer que l’analyse du code pour le projet utilise le jeu de règles approprié :  
  
- Si la stratégie d’archivage utilise un des ensembles de règles intégrés Microsoft, ouvrez la boîte de dialogue Propriétés du projet de code, afficher la page analyse du Code et sélectionnez la règle définie dans la page analyse du Code, les code des paramètres de projet. L’ensembles de règles standard sont automatiquement installés avec Visual Studio de Microsoft sont la valeur est en lecture seule et ne doit pas être modifié. Si les ensembles de règles ne sont pas modifiés, les règles dans la stratégie et les ensembles de règles locales sont garantis pour correspondre.  
  
- Si la stratégie d’archivage utilise un ensemble de règles personnalisé, effectuer une opération get sur le fichier d’ensemble de règles dans le contrôle de version pour créer une copie locale. Spécifiez ensuite cet emplacement local dans les paramètres d’analyse de code pour le projet de code. Les règles sont garanties à faire correspondre si l’ensemble de règles pour la stratégie d’archivage est à jour.  
  
     Si vous mappez l’emplacement de contrôle de version dans un dossier local qui se trouve dans la même relation à la racine de projet d’équipe que votre projet de code, l’emplacement de la règle est défini à l’aide d’un chemin d’accès relatif. Le chemin d’accès relatif permet de s’assurer que le paramètre de projet de code pour l’analyse du code peut être déplacé vers d’autres ordinateurs.  
  
- Personnaliser une copie de l’ensemble de règles pour la stratégie d’archivage pour un projet de code. Assurez-vous que le nouvel ensemble de règles contient toutes les règles dans la stratégie d’archivage et les autres règles que vous souhaitez inclure. Il se peut que vous devez vous assurer que votre ensemble de règles inclut toutes les règles dans l’ensemble de règles pour la stratégie d’archivage.  
  
### <a name="to-specify-a-microsoft-standard-rule-set"></a>Pour spécifier une règle standard Microsoft défini  
  
1. Dans **l’Explorateur de solutions**, cliquez sur le projet de code, puis cliquez sur **propriétés**.  
  
2. Cliquez sur **analyse du Code**.  
  
3. Dans le **exécuter cet ensemble de règles** , cliquez sur l’ensemble de règles de stratégie d’archivage.  
  
### <a name="to-specify-a-custom-check-in-policy-rule-set"></a>Pour spécifier un ensemble de règles de stratégie d’archivage personnalisées  
  
1. Si nécessaire, effectuer une opération get sur le fichier d’ensemble de règle qui spécifie la stratégie d’archivage.  
  
2. Dans **l’Explorateur de solutions**, cliquez sur le projet de code, puis cliquez sur **propriétés**.  
  
3. Cliquez sur **analyse du Code**.  
  
4. Dans le **exécuter cet ensemble de règles** , cliquez sur  **\<Parcourir... >** .  
  
5. Dans le **Open** boîte de dialogue, spécifiez la règle de stratégie d’archivage définie le fichier.  
  
### <a name="to-create-a-custom-rule-set-for-a-code-project"></a>Pour créer une règle personnalisée définie pour un projet de code  
  
1. Suivez une des procédures plus haut dans cette rubrique pour sélectionner la stratégie d’archivage du projet d’équipe dans la page d’analyse du Code de la boîte de dialogue des paramètres de projet.  
  
2. Cliquez sur **Ouvrir**.  
  
3. Ajouter ou supprimer des règles à l’aide de l’éditeur d’ensemble de règles.  
  
     Pour plus d’informations, consultez [création d’ensembles de règles personnalisés](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
4. Enregistrer la règle modifiée définie dans un fichier .ruleset sur l’ordinateur local ou sur un chemin d’accès UNC.  
  
5. Ouvrir la boîte de dialogue Propriétés du projet de code et afficher le **analyse du Code** page.  
  
6. Dans le **exécuter cet ensemble de règles** , cliquez sur  **\<Parcourir... >** .  
  
7. Dans le **Open** boîte de dialogue, spécifiez l’ensemble de règles fichier.
