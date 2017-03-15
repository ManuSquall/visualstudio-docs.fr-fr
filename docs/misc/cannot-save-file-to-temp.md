---
title: "Impossible d’enregistrer le fichier dans TEMP | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrID735"
ms.assetid: 1055fc15-9641-43b2-a40c-a0a9fbbb34b2
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible d’enregistrer le fichier dans TEMP
Soit un composant ne trouve pas de répertoire nommé TEMP, soit le lecteur ou la partition contenant le répertoire TEMP ne dispose pas de suffisamment d’espace pour enregistrer les informations.  
  
### Pour corriger cette erreur  
  
1.  Créez un répertoire nommé « TEMP » et affectez son chemin comme valeur de la variable d’environnement TEMP.  
  
2.  Libérez de l’espace sur le disque en supprimant des fichiers inutiles ou créez un répertoire TEMP sur une autre partition et affectez son chemin comme valeur de la variable d’environnement TEMP.  
  
## Voir aussi  
 [Error Types](/dotnet/visual-basic/programming-guide/language-features/error-types)