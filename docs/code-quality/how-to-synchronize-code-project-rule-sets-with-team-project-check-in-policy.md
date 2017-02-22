---
title: "Comment&#160;: synchroniser des ensembles de r&#232;gles applicables &#224; des projets de code avec la strat&#233;gie d&#39;archivage du projet d&#39;&#233;quipe | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.selecttfsruleset"
ms.assetid: 9b02f934-2db6-41ec-aaff-9c31ceec2f04
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: synchroniser des ensembles de r&#232;gles applicables &#224; des projets de code avec la strat&#233;gie d&#39;archivage du projet d&#39;&#233;quipe
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous synchronisez les paramètres d'analyse du code des projets de code avec la stratégie d'archivage du projet d'équipe en spécifiant un ensemble de règles qui contient au moins les règles spécifiées dans l'ensemble de règles de la stratégie d'archivage.  Votre développeur sénior peut vous indiquer le nom et l'emplacement de l'ensemble de règles pour la stratégie d'archivage.  Vous pouvez utiliser l'une des options suivantes pour garantir que l'analyse du code du projet utilise le jeu de règles approprié :  
  
-   Si la stratégie d'archivage utilise l'un des ensembles de règles prédéfinis Microsoft, ouvrez la boîte de dialogue des propriétés du projet de code, affichez la page Analyse du code et sélectionnez\-le dans la page Analyse du code des paramètres du projet de code.  Les ensembles de règles standards Microsoft sont installés automatiquement avec Visual Studio ; ils sont en lecture seule et ne doivent pas être modifiés.  Si les ensembles de règles ne sont pas modifiés, la correspondance entre les règles comprises dans la stratégie et les ensembles de règles locaux est garantie.  
  
-   Si la stratégie d'archivage utilise un ensemble de règles personnalisé, exécutez une opération d'extraction sur le fichier d'ensemble de règles dans le contrôle de version pour créer une copie locale.  Spécifiez ensuite cet emplacement local dans les paramètres d'analyse du code pour le projet de code.  La correspondance des règles est garantie si l'ensemble de règles pour la stratégie d'archivage est à jour.  
  
     Si vous mappez l'emplacement de contrôle de version à un dossier local qui entretient la même relation avec la racine de projet d'équipe que votre projet de code, l'emplacement de l'ensemble de règles est défini à l'aide d'un chemin d'accès relatif.  Le chemin d'accès relatif garantit que le paramètre de projet de code pour l'analyse du code peut être transmis à d'autres ordinateurs.  
  
-   Personnalisez une copie de l'ensemble de règles pour la stratégie d'archivage d'un projet de code.  Assurez\-vous que le nouvel ensemble de règles contient toutes les règles de la stratégie d'archivage et toute autre règle que vous souhaitez inclure.  Vous devez vous assurer que votre ensemble de règles inclut toutes les règles dans l'ensemble de règles pour la stratégie d'archivage.  
  
### Pour spécifier un ensemble de règles Microsoft standard  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le projet de code, puis cliquez sur **Propriétés**.  
  
2.  Cliquez sur **Analyse du code**.  
  
3.  Dans la liste **Exécuter cet ensemble de règles**, cliquez sur l'ensemble de règles de la stratégie d'archivage.  
  
### Pour spécifier un ensemble de règles de stratégie d'archivage personnalisé  
  
1.  Si nécessaire, exécutez une opération d'extraction sur le fichier d'ensemble de règles qui spécifie la stratégie d'archivage.  
  
2.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le projet de code, puis cliquez sur **Propriétés**.  
  
3.  Cliquez sur **Analyse du code**.  
  
4.  Dans la liste **Exécuter cet ensemble de règles**, cliquez sur **\<Parcourir...\>**.  
  
5.  Dans la boîte de dialogue **Ouvrir**, spécifiez le fichier de l'ensemble de règles de la stratégie d'archivage.  
  
### Pour créer un ensemble de règles personnalisé pour un projet de code  
  
1.  Suivez l'une des procédures présentées précédemment dans cette rubrique pour sélectionner la stratégie d'archivage du projet d'équipe dans la page Analyse du code de la boîte de dialogue des paramètres du projet.  
  
2.  Cliquez sur **Ouvrir**.  
  
3.  Ajoutez ou supprimez des règles à l'aide de l'éditeur d'ensembles de règles.  
  
     Pour plus d'informations, consultez [Création d'ensembles de règles personnalisés](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
4.  Enregistrez l'ensemble de règles modifié dans un fichier .ruleset sur l'ordinateur local ou dans un chemin d'accès UNC.  
  
5.  Ouvrez la boîte de dialogue des propriétés du projet de code et affichez la page **Analyse du code**.  
  
6.  Dans la liste **Exécuter cet ensemble de règles**, cliquez sur **\<Parcourir...\>**.  
  
7.  Dans la boîte de dialogue **Ouvrir**, spécifiez le fichier de l'ensemble de règles.