---
title: "Comment&#160;: comparer des fichiers de donn&#233;es du profileur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vsperf.choosediffbinaries"
helpviewer_keywords: 
  - "fichiers de résultats du profileur, comment comparer"
  - "outils de profilage, comment comparer des fichiers de résultats du profileur"
ms.assetid: 1905b45d-c6b3-43c8-87b1-1aee734f37f9
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# Comment&#160;: comparer des fichiers de donn&#233;es du profileur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez comparer les résultats de deux fichiers de données du profileur \(.vsp ou .vsps\) en créant un rapport \(Diff\) ou un affichage de comparaison.  La comparaison affiche les différences, régressions de performance et améliorations qui sont apparues entre deux sessions de profilage.  
  
 Le rapport Diff présente un affichage tabulaire des données.  Le tableau présente le delta ou changement de la ligne de base.  Celui\-ci est calculé en déterminant la différence entre l'ancienne valeur, la valeur de base et la valeur de résultat à partir de la nouvelle analyse.  
  
 Les comparaisons de données de profileur peuvent être basées sur les fonctions dans le code, les modules de l'application, les lignes, les pointeurs d'instruction \(IP\) et les types.  
  
 Un seuil peut être défini pour réduire le bruit et éliminer par filtrage toutes les données de l'affichage tabulaire des lignes qui n'ont pas été modifiées par une valeur spécifiée.  
  
### Pour créer la vue Fichier de comparaison pour un projet dans l'Explorateur de performances  
  
1.  Dans l' **Explorateur de performances**, sous **Rapports**, sélectionnez le fichier de rapport .vsp ou .vsps que vous voulez utiliser comme valeurs de base pour la comparaison.  
  
2.  Sélectionnez les fichiers de rapport .vsp ou .vsps que vous souhaitez comparer.  
  
3.  Cliquez avec le bouton droit sur l'un des fichiers sélectionnés, puis cliquez sur **Comparer les rapports**.  
  
### Pour comparer les valeurs  
  
1.  Sélectionnez l'onglet **Rapport de comparaison** dans la fenêtre Vue Rapport.  
  
2.  Dans la liste déroulante **Tableau**, sélectionnez la fonction ou les modules à comparer.  
  
3.  Dans la liste déroulante **Colonne**, sélectionnez la valeur que vous souhaitez comparer.  
  
4.  \(facultatif\) Tapez une valeur pour **Seuil**.  
  
5.  Cliquez sur **Appliquer**.  
  
### Pour comparer les fichiers de rapport  
  
1.  Dans le menu **Analyser** , sélectionnez **Comparer les rapports de performances**.  
  
2.  Dans la fenêtre **Sélectionner les fichiers d'analyse à des fins de comparaison**, recherchez et sélectionnez le fichier d'analyse **Fichier de base** \(.vsp ou .vsps\) et le **Fichier de comparaison** \(.vsp ou .vsps\).  
  
3.  Cliquez sur **OK**.