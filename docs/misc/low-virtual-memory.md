---
title: "M&#233;moire virtuelle faible | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aec803b1-9d76-46bb-8f14-8c63d80112a5
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# M&#233;moire virtuelle faible
Ce message s'affiche lorsque la mémoire virtuelle est faible et [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] cesse de répondre.  Toutefois, cette erreur ne se produit pas lorsque la mémoire virtuelle sur votre ordinateur est faible mais plutôt lorsque [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] exécute hors de l'espace d'adressage.  Le plus souvent, cette erreur se produit sur les ordinateurs qui exécutent les systèmes d'exploitation 32 bits, qui limitent [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] à 2 Go d'espace d'adressage.  Lorsque vous travaillez avec les processus 32 bits, l'application peut adresser uniquement 4 Go de mémoire \(bits 2^32\).  Toutefois, les versions 32 bits de Windows réservent 2 Go d'espace d'adressage virtuel d'un processus pour les besoins internes \(par exemple, pour travailler avec d'autres pilotes système de l'ordinateur la carte graphique ou\).  Par conséquent, le processus 32 bits peut utiliser uniquement 2 Go pour ses besoins internes.  Les utilisateurs peuvent définir le commutateur \/3GB pour garantir que les fenêtres réserve uniquement 1 Go pour lui\-même et donne 3 Go au processus.  Dans la plupart des cas, les performances ne diminue pas avec une limite de seulement 1 Go pour Windows.  
  
 Sur les systèmes qui exécutent les versions 64 bits de Windows, cette erreur se produit rarement car le processus peut utiliser chacun des 4 Go d'espace adressables, et les fenêtres peuvent utiliser les adresses mémoire 64 bits pour le matériel et les pilotes système.  Toutefois, l'utilisation de la mémoire peut dépasser 3 GB voire 4 GB lorsque [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] traite des groupes de données.  Pour plus d'informations,[consultez Visual Studio : Pourquoi y a aucune version 64 bits ? \(mais\)](http://go.microsoft.com/fwlink/?LinkId=246307).  
  
 Cette erreur se produit généralement lorsque [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] met grandes quantités de données ou de plusieurs processus en cache nécessitant beaucoup de mémoire.  
  
 Les scénarios suivants impliquent mettre en cache une grande quantité de données, et vous pouvez généralement les résoudre en redémarrant [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Exécution [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour la première fois après installation.  
  
-   Installation ou désinstallation d'une extension.  
  
-   Sélection ou personnalisation des éléments dans **Boîte à outils**.  
  
-   Modification de vos paramètres d'[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Permettre au système pour passer en mode de veille \(hibernez\) tandis que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] est ouvert.  
  
 Les scénarios suivants nécessitent une quantité importante de mémoire active.  Dans ces cas, nous vous recommandons d'exécuter [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] avec uniquement des éléments essentiels ou les processus supplémentaires en cours de exécution dans une deuxième instance de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Création de solutions de taille importante.  
  
-   Utilisation de grands documents XML.  
  
-   Mise à niveau d'une version antérieure d'[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Reciblage des solutions.  
  
-   Exécution d'[!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] en modifiant le code.  
  
-   Exécution d'IntelliTrace sur plusieurs projets à la fois.  
  
 Si ces actions n'empêchent pas l'erreur, vous pouvez augmenter votre espace d'adressage disponible sur un système qui exécute [!INCLUDE[win7](../debugger/includes/win7_md.md)] si vous exécutez bcedit.exe avec la syntaxe suivante :  
  
 **bcdedit \/set IncreaseUserVa 3072**  
  
 Cette commande permet d'augmenter l'allocation de mémoire virtuelle en mode utilisateur de 2 GB à 3 GB sur un système de Go.  Si vous ajoutez le commutateur \/3GB, le système entier peut traiter plus de mémoire et donner à chaque application un pourcentage supérieur de la mémoire.  
  
> [!NOTE]
>  Vous devez exécuter bcdedit.exe avec des autorisations d'administration.  Si le chiffrement BitLocker est activé, vous devez l'interrompre, apportez les modifications, redémarrez le système, puis réactiver Bitlocker.  
  
 Même si vous augmentez l'allocation de mémoire virtuelle à 3 Go, cette erreur peut se reproduire car seule application en peuvent toujours utiliser uniquement 2 Go de mémoire virtuelle.  Si cette erreur continue à apparaître, réduisez la taille de votre solution, puis redémarrez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Vous pouvez réduire votre solution l'un ou l'autre de ces refactoriser par pour supprimer les projets qui sont utilisés rarement ou par le déchargement des projets qui ne sont pas nécessaires.  Si l'erreur se produit lorsque vous générez votre solution, essayez la générer à une invite de commandes.  
  
## Voir aussi  
 [Resources for Troubleshooting IDE Errors](../ide/reference/resources-for-troubleshooting-integrated-development-environment-errors.md)