---
title: "Comment&#160;: d&#233;finir les options de nom de fichier de donn&#233;es de profilage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d7a8d6b9-ab23-46fb-98ed-774781157860
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Comment&#160;: d&#233;finir les options de nom de fichier de donn&#233;es de profilage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Par défaut, vous enregistrez un fichier de données de profilage \(.vsp\) à l'aide de la syntaxe suivante :  
  
 *Chemin d'accès\\Fichier VSP\\AAMMJJ \(N\)* **.vsp**  
  
 Vous pouvez modifier les paramètres d'attribution de nom dans la page Général de la boîte de dialogue de propriétés pour la session de performance.  
  
 **Configuration requise**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
|||  
|-|-|  
|*Chemin d'accès*|Répertoire qui contient le rapport.  L'emplacement par défaut est le dossier de la solution ou l'emplacement par défaut pour les projets et solutions de l'utilisateur.|  
|*Fichier VSP*|Nom du fichier de données de profilage.  Le nom par défaut est le nom de la solution ou du fichier exécutable profilé\(e\).|  
|*AAMMJJ*|Horodatage qui affiche l'année, le mois et le jour auxquels les données de profilage ont été collectées.|  
|*\(N\)*|S'il existe plusieurs fichiers de données de profilage, un nombre incrémenté est ajouté au nom du fichier entre parenthèses.|  
  
### Pour modifier la syntaxe d'attribution de nom des fichiers de données de profilage d'une session de performance  
  
1.  Dans l'**Explorateur de performances**, cliquez avec le bouton droit sur le nom de la session de performance, puis cliquez sur **Propriétés**.  
  
2.  Cliquez sur **Général**.  
  
3.  Sous **Rapport**, modifiez les paramètres suivants au besoin :  
  
    |||  
    |-|-|  
    |**Emplacement du rapport**|Spécifiez un répertoire pour le stockage des fichiers de données de profilage.|  
    |**Nom du rapport**|Spécifiez un nom de base pour les fichiers.|  
    |**Ajouter automatiquement de nouveaux rapports à la session**|Activez la case à cocher pour ajouter automatiquement le fichier de données à la session de performance.|  
    |**Ajouter un numéro à incrémentation aux rapports générés**|Activez la case à cocher pour ajouter un numéro à incrémentation au nom du fichier lorsqu'il existe plusieurs fichiers du même nom.  Désactivez la case à cocher pour remplacer un fichier existant.|  
    |**Utiliser un horodatage pour le nombre**|Activez la case à cocher pour ajouter un horodatage au nom du fichier.|