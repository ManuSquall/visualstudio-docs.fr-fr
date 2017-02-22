---
title: "Zone de test 2&#160;: Obtenir &#224; partir du contr&#244;le de code Source | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "contrôle de source de plug-ins, l’obtention d’éléments à partir du contrôle de code source"
  - "contrôle de code source (Visual Studio SDK), l’obtention d’éléments à partir de"
ms.assetid: cbd345c5-ca43-4630-b7a4-85564f4e2090
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# Zone de test 2&#160;: Obtenir &#224; partir du contr&#244;le de code Source
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cette zone de test traite des cas de test permettant de récupérer des éléments de la banque des versions via la commande Get. Ces cas de test peut être appliqués aux locaux et aux projets Web.  
  
## Accès au Menu de commande  
 Les éléments suivants [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] menu chemins d’environnement de développement intégré sont utilisés dans les cas de test.  
  
##### Obtenir la dernière Version :  
  
-   **Fichier**, **contrôle de code Source**, **obtenir la dernière Version**.  
  
-   **Fichier**, **obtenir la dernière Version**.  
  
-   Menu contextuel, **obtenir la dernière Version**.  
  
-   Get : **fichier**, **contrôle de code Source**, **obtenir**.  
  
## Comportement attendu  
  
##### Obtenir la dernière Version :  
 Effectue une extraction silencieuse \(sans interface utilisateur\) de la dernière version de l’élément à partir de la banque des versions.  
  
##### Get :  
 Affiche la **obtenir** boîte de dialogue et permet à l’utilisateur d’apporter des modifications à l’ensemble de fichiers qui est récupérée ainsi que pour modifier les options qui affectent la façon dont les fichiers sont récupérés.  
  
## Cas de test  
  
|Action|Étapes de test|Résultats attendus à vérifier|  
|------------|--------------------|-----------------------------------|  
|Obtenir la dernière Version d’un fichier qui n’existe pas localement|1.  Créez un projet.<br />2.  Ajouter un élément au projet.<br />3.  Placer le projet sous contrôle de code source.<br />4.  Supprimer la copie locale de l’élément.<br />5.  Obtenir la dernière Version de l’élément \(Menu contextuel, **obtenir la dernière Version**\).|Fichier d’élément est récupéré localement.|  
|Obtenir un fichier qui n’existe pas localement|1.  Créez un projet.<br />2.  Ajouter un élément au projet.<br />3.  Placer le projet sous contrôle de code source.<br />4.  Supprimer la copie locale de l’élément.<br />5.  Obtenir l’élément \(**fichier**, **contrôle de code Source**, **obtenir** \< élément \>\).|Fichier d’élément est récupéré localement.|  
|Obtenir un fichier qui a été extrait en mode exclusif et modifié localement|1.  Créez un projet.<br />2.  Ajouter un élément au projet.<br />3.  Placer le projet sous contrôle de code source.<br />4.  Extrayez l’élément de projet de manière exclusive.<br />5.  Modifier la copie locale.<br />6.  Obtenir la dernière Version de l’élément \(**fichier**, **obtenir la dernière Version de** \< élément \>\). Si cette étape réussit, passez à l’étape suivante.<br />7.  Cliquez sur **remplacer** bouton dans la boîte de dialogue d’avertissement.|**ReResult à l’étape 6** `:`<br /><br /> Boîte de dialogue d’avertissement indique que ce fichier est extrait.<br /><br /> **ReResult de l’étape 7 :**<br /><br /> Modification de fichier local est remplacé par la version d’origine à partir de la banque des versions.<br /><br /> Fichier est en lecture\/écriture.|  
|Obtenez et remplacez le fichier est extrait, partagé et modifiée localement|1.  Créer un nouveau projet.<br />2.  Ajouter un élément au projet.<br />3.  Placer le projet sous contrôle de code source.<br />4.  Consultez l’élément de projet partagé.<br />5.  Modifier la copie locale.<br />6.  Obtenir la dernière Version de l’élément \(**fichier**, **obtenir la dernière Version de** \< élément \>\). Si cette étape réussit, passez à l’étape suivante.<br />7.  Cliquez sur **remplacer** dans la boîte de dialogue d’avertissement.|**Résultat de l’étape 6 :**<br /><br /> Boîte de dialogue d’avertissement indique que ce fichier est extrait.<br /><br /> **Résultat de l’étape 7 :**<br /><br /> Modification de fichier local est remplacé par la version d’origine à partir de la banque des versions.<br /><br /> Fichier est en lecture\/écriture.|  
|Obtenir un fichier qui n’existe pas localement, même en tant que la version la plus récente dans la banque des versions|1.  Créer un nouveau projet.<br />2.  Ajouter un élément au projet.<br />3.  Placer le projet sous contrôle de code source.<br />4.  Obtenir l’élément \(**fichier**, **contrôle de code Source**, **obtenir** \< élément \>\).|Fichier local est inchangé.|  
|Obtenir une solution avec un projet|1.  Créer une solution avec un projet.<br />2.  Placez la solution sous contrôle de code source.<br />3.  Supprimez tous les fichiers projet localement.<br />4.  Obtention de la solution \(**fichier**, **contrôle de code Source**, **obtenir**\).|Tous les fichiers supprimés sont restaurées localement.|  
  
## Voir aussi  
 [Guide d'évaluation pour les Plug\-ins de contrôle de code Source](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)