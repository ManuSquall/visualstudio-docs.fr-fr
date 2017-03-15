---
title: "Avertissements VSInstr | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "instrumentation, VSInstr (outil)"
  - "outils d'analyse des performances, VSInstr (outil)"
  - "VSInstr (outil)"
  - "avertissements"
  - "avertissements, VSInstr (outil)"
ms.assetid: 47512bc9-a8e9-4628-883a-d9888edab786
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Avertissements VSInstr
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le tableau suivant répertorie les avertissements émis par l'outil VSInstr.exe.  Vous pouvez utiliser l'option NOWARN avec les numéros d'avertissement pour empêcher l'affichage de l'avertissement.  
  
|Numéro d'avertissement|Description|  
|----------------------------|-----------------|  
|**VSP2000**|Erreur interne.  Impossible d'obtenir le nom de fichier du module de cet exécutable.|  
|**VSP2001**|\<NomAssembly\> est un assembly à nom fort.  Vous devez le resigner avant de l'exécuter.<br /><br /> Cet avertissement se produit lorsqu'un assembly signé est instrumenté.  Vous pouvez utiliser l'outil sn.exe pour signer de nouveau le fichier binaire ou désactiver temporairement la spécification de nom fort.  Pour plus d'informations, consultez [Sn.exe \(Strong Name Tool\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md).|  
|**VSP2002**|Impossible de trouver la fonction \<NomFonction\> dans le fichier \<NomFichier\><br /><br /> Cet avertissement se produit si une fonction ne peut pas être retrouvée dans le fichier spécifié.|  
|**VSP2003**|Impossible de trouver des sauts croisés vers la fonction \<NomFonction\> dans le fichier \<NomFichier\>.<br /><br /> Cet avertissement se produit si VSInstr ne peut pas annuler les sauts croisés.  Les sauts croisés sont utilisés pour l'optimisation du code.|  
|**VSP2004**|La fonction \<NomFonction\> a été exclue à l'aide du commutateur de ligne de commande EXCLUDE mais était requise parce qu'elle contenait un saut croisé.<br /><br /> Cet avertissement se produit si la fonction a été exclue à l'aide de l'option EXCLUDE mais est nécessaire pendant le processus d'instrumentation.  Le profileur inclut automatiquement la fonction requise.|  
|**VSP2005**|Erreur d'instrumentation interne \<TextErreur\><br /><br /> Cet avertissement est émis si l'instrumentation ne peut pas être exécutée.  Consultez le texte de l'erreur pour déterminer si elle peut être corrigée.|  
|**VSP2006**|Impossible de localiser le fichier PDB de \<nom\><br /><br /> Cet avertissement se produit si le fichier PDB n'existe pas dans le chemin de recherche ou ne correspond pas au binaire.|  
|**VSP2007**|\<NomFichier\> ne contient aucun code instrumentable.<br /><br /> Cet avertissement est émis si les fonctions du fichier binaire étaient toutes exclues ou si le fichier spécifié ne contient que des ressources.|  
|**VSP2008**|Impossible d'obtenir les attributs de sécurité de \<nom\>.  Code d'erreur \<code\><br /><br /> Cet avertissement se produit si l'utilisateur n'a pas l'autorisation READ\_DAC.  Lors du processus d'instrumentation, le profileur essaie de conserver la liste DACL d'origine du binaire.  Étant donné que le binaire d'origine est remplacé par un nouveau binaire, la liste DACL du binaire d'origine doit être copiée et appliquée au nouveau binaire.  Cette opération peut échouer si l'utilisateur n'a pas l'accès READ\_DAC sur le binaire d'origine.|  
|**VSP2009**|Impossible de définir des attributs de sécurité dans \<nom\>.  Code d'erreur \<NuméroErreur\><br /><br /> Cet avertissement se produit si l'utilisateur n'a pas l'autorisation WRITE\_DAC.  Lors du processus d'instrumentation, le profileur essaie de conserver la liste DACL d'origine du binaire.  Étant donné que le binaire d'origine est remplacé par un nouveau binaire, la liste DACL du binaire d'origine doit être copiée et appliquée au nouveau binaire.  Cette opération peut échouer si l'utilisateur n'a pas l'accès WRITE\_DAC sur le nouveau binaire.|  
|**VSP2010**|Aucune fonction n'a été spécifiquement sélectionnée pour l'instrumentation en raison des options \-INCLUDE\/\-EXCLUDE|  
|**VSP2011**|La fonction funcspec Include\/Exclude \<nom\> ne correspond à aucune fonction|  
|**VSP2012**|L'image ne renferme aucun code susceptible d'être instrumenté pour une couverture du code.<br /><br /> Le profileur n'instrumente pas le type de code suivant :<br /><br /> -   Fonctions CRT statiques<br />-   Méthodes managées attribuées avec NonUserCodeAttribute<br />-   Méthodes managées attribuées avec DebuggerHiddenAttribute<br />-   Blocs MASM<br /><br /> Cet avertissement est généré si, après ce filtrage, il ne reste aucun code.|  
|**VSP2013**|Vous devez exécuter cette image en tant que processus 32 bits pour pouvoir l'instrumenter.  Les indicateurs dans l'en\-tête CLR ont été mis à jour pour en tenir compte.<br /><br /> Le générateur de profils modifie le binaire afin que les systèmes d'exploitation 64 bits puissent ouvrir le processus 32 bits dans l'émulateur WOW64.  Pour les bibliothèques \(DLL\), cette opération peut échouer en cas de chargement dans un processus 64 bits existant.  Cet avertissement notifie l'utilisateur de la dépendance.|  
|**VSP2014**|L'image instrumentée obtenue ne semble ne pas valide et risque de ne pas s'exécuter.<br /><br /> Ce message se produit lorsque l'assembly instrumenté final a un en\-tête PE non valide.|  
  
## Voir aussi  
 [VSInstr](../profiling/vsinstr.md)