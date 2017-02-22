---
title: "DA0030&#160;: collecter les mesures d&#39;interaction de couche pour les projets de base de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.DA0030"
  - "vs.performance.rules.DA0030"
  - "vs.performance.30"
ms.assetid: 42b2f69d-0cfa-4854-82c4-589c3d8b4557
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# DA0030&#160;: collecter les mesures d&#39;interaction de couche pour les projets de base de donn&#233;es
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|ID de la règle|DA0030|  
|Catégorie|Utilisation des outils de profilage|  
|Méthode de profilage|Échantillonnage|  
|Message|La collecte des mesures d'interaction pour les applications multicouches vous aidera à comprendre les modèles d'utilisation de la base de données et les retards d'accès aux données de clé.  Profilez de nouveau l'application en activant l'option Profilage d'interaction de couche.|  
|Type de règle|Information|  
  
## Cause  
 Les appels à des méthodes <xref:System.Data> représentent une proportion significative des données de profilage et vous n'avez pas collecté de données sur l'interaction de couche durant l'exécution du profilage.  Envisagez un autre profilage et l'ajout de données sur l'interaction de couche.  
  
## Description de la règle  
 Cette règle se déclenche à chaque activité significative dans les fonctions qui résident dans les espaces de noms System.Data, notamment <xref:System.Data.Linq> <xref:System.Data.Linq>.  
  
 Les applications multicouches utilisent des services superposés pour leurs couches présentation et données.  Souvent la couche données est un processus distinct qui exécute un système de gestion de base de données tel que Microsoft SQL Server.  La couche données peut même s'exécuter sur un ordinateur séparé du reste de l'application.  L'échantillonnage de profils fournit très peu d'informations sur les fonctions et services exécutés hors processus ou à distance.  
  
 Les outils de profilage peuvent rassembler les informations de minutage pour les applications multicouches qui interagissent avec une couche données Microsoft SQL Server à l'aide des appels asynchrones aux services ADO.NET.  Vous devez activer explicitement le profilage d'interaction de couche.  Il n'est pas activé par défaut.  
  
## Comment corriger les violations  
 Cette règle est fournie uniquement à titre d'information et peut ne pas exiger d'action corrective.  
  
 Pour plus d'informations sur l'ajout de données sur l'interaction de couche aux données de profilage à partir de l'IDE Visual Studio, consultez [Collecte de données d’interaction de couche](../profiling/collecting-tier-interaction-data.md).  Pour plus d'informations sur l'ajout de données sur l'interaction de couche à partir de la ligne de commande, consultez [Collecte de données d’interaction de couche](../profiling/adding-tier-interaction-data-from-the-command-line.md).