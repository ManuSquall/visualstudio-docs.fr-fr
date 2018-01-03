---
title: CodeIndex, commande | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- command-line tools [Team Foundation Server]
- TFSConfig
- CodeIndex command [Team Foundation Server]
ms.assetid: b79568d4-6a64-4ca9-a1ee-3e57f92a9c5c
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3f181dccce6239cc8014e8e8ebf54c2e53794a50
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="codeindex-command"></a>CodeIndex, commande
Utilisez la commande **CodeIndex** pour gérer l’indexation de code dans Team Foundation Server. Par exemple, vous pouvez réinitialiser l'index pour corriger des informations CodeLens ou pour désactiver l'indexation afin d'analyser les problèmes de performances du serveur.  
  
 **Autorisations requises**  
  
 Pour utiliser la commande **CodeIndex**, vous devez être membre du groupe de sécurité **Team Foundation Administrators**. Consultez [Autorisations et groupes définis pour Team Services et TFS](https://www.visualstudio.com/docs/setup-admin/permissions).  
  
> [!NOTE]
>  Même si vous vous connectez en tant qu'administrateur, vous devez ouvrir une fenêtre d'invite de commandes avec élévation de privilèges pour exécuter cette commande. Vous devez également exécuter cette commande depuis la couche Application pour Team Foundation.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
TFSConfig CodeIndex /indexingStatus | /setIndexing:[ on | off | keepupOnly ] | /ignoreList:[ add | remove | removeAll | view ] ServerPath | /listLargeFiles [/fileCount:FileCount] [/minSize:MinSize] | /reindexAll | /destroyCodeIndex [/noPrompt] | /temporaryDataSizeLimit:[ view | <SizeInGBs> | disable ] | /indexHistoryPeriod:[ view | all | <NumberOfMonths> ] [/collectionName:CollectionName | /collectionId:CollectionId]  
```  
  
#### <a name="parameters"></a>Paramètres  
  
|**Argument**|**Description**|  
|------------------|---------------------|  
|`CollectionName`|Spécifie le nom de la collection du projet d’équipe. Si le nom contient des espaces, placez-le entre guillemets, par exemple "Fabrikam Web Site".|  
|`CollectionId`|Spécifie le numéro d'identification de la collection de projets d'équipe.|  
|`ServerPath`|Spécifie le chemin d’accès d’un fichier de code.|  
  
|**Option**|**Description**|  
|----------------|---------------------|  
|**/indexingStatus**|Affichez l'état et la configuration du service d'indexation de code.|  
|**/setIndexing:**[ on &#124; off &#124; keepupOnly ]|-   **on** : démarrer l’indexation de tous les ensembles de modifications.<br />-   **off** : arrêter l’indexation de tous les ensembles de modifications.<br />-   **off** : arrêter l’indexation des ensembles de modifications créés précédemment et commencer l’indexation de nouveaux ensembles de modifications uniquement.|  
|**/ignoreList:**[ add &#124; remove &#124; removeAll &#124; view ] `ServerPath`<br /><br /> Vous pouvez utiliser le caractère générique (*) au début, à la fin ou aux deux extrémités du chemin d’accès au serveur.|Spécifie une liste de fichiers de code et leurs chemins d’accès à ne pas indexer.<br /><br /> -   **add** : ajouter le fichier à ne pas indexer à la liste des fichiers ignorés.<br />-   **remove** : supprimer le fichier à indexer de la liste des fichiers ignorés.<br />-   **removeAll** : effacer la liste des fichiers ignorés et démarrer l’indexation de tous les fichiers.<br />-   **view** : afficher tous les fichiers qui ne sont pas indexés.|  
|**/listLargeFiles [/fileCount:** `FileCount` **/minSize:** `MinSize`]|Indique le nombre spécifié de fichiers qui dépassent la taille spécifiée en Ko. Vous pouvez ensuite utiliser l’option **/ignoreList** pour exclure ces fichiers de l’indexation.|  
|**/reindexAll**|Effacez les données indexées précédemment et redémarrez l'indexation.|  
|**/destroyCodeIndex [/noPrompt]**|Supprimez l'index de code et supprimez toutes les données indexées. Confirmation inutile si vous utilisez l’option **/noPrompt**.|  
|**/temporaryDataSizeLimit**:[ view &#124; <`SizeInGBs`> &#124; disable ]|Contrôle la quantité de données temporaires que CodeLens crée lors du traitement des ensembles de modifications. La limite par défaut est 2 Go.<br /><br /> -   **view** : afficher la limite de taille actuelle.<br />-   `SizeInGBs` : modifier la limite de taille.<br />-   **disable** : supprimer la limite de taille.<br /><br /> Cette limite est vérifiée avant que CodeLens ne traite un nouvel ensemble de modifications. Si les données temporaires dépassent cette limite, CodeLens suspend le traitement des ensembles de modifications passés, pas celui des nouveaux. CodeLens redémarre le traitement une fois que les données sont nettoyées et que leur taille est inférieure à cette limite. Le nettoyage s'exécute automatiquement une fois par jour. Cela signifie que les données temporaires peuvent dépasser cette limite tant que l'opération de nettoyage n'a pas commencé.|  
|**/indexHistoryPeriod**:[ view &#124; all &#124; <`NumberOfMonths`> ]|Contrôler la durée d'indexation de votre historique des modifications. Cela affecte la quantité d'historique que CodeLens affiche. La limite par défaut est 12 mois. Cela signifie que l'historique des modifications affiché par CodeLens englobe uniquement les 12 derniers mois.<br /><br /> -   **view** : afficher le nombre de mois actuel.<br />-   **all** : indexer tout l’historique des modifications.<br />-   `NumberOfMonths` : modifier le nombre de mois utilisés pour indexer l’historique des modifications.|  
|**/collectionName:** `CollectionName`|Spécifie le nom de la collection de projets d’équipe sur laquelle exécuter la commande **CodeIndex**. Nécessaire si vous n’utilisez pas **/CollectionId**.|  
|**/collectionId :** `CollectionId`|Spécifie le numéro d’identification de la collection de projets d’équipe sur laquelle exécuter la commande **CodeIndex**. Nécessaire si vous n’utilisez pas **/CollectionName**.|  
  
## <a name="examples"></a>Exemples  
  
> [!NOTE]
>  Les noms de sociétés, d'organisations, de produits, de domaines, d'adresses de messagerie, de logos, de personnes, de lieux et d'événements mentionnés dans les exemples sont fictifs.  Toute ressemblance avec des noms ou des événements réels est purement fortuite et involontaire.  
  
 Pour consulter l'état et la configuration d'indexation du code :  
  
```  
TFSConfig CodeIndex /indexingStatus /collectionName:"Fabrikam Web Site"  
```  
  
 Pour démarrer l'indexation de tous les ensembles de modifications :  
  
```  
TFSConfig CodeIndex /setIndexing:on /collectionName:"Fabrikam Web Site"  
```  
  
 Pour arrêter l'indexation des ensembles de modifications créés précédemment et commencer l'indexation de nouveaux ensembles de modifications uniquement :  
  
```  
TFSConfig CodeIndex /setIndexing:keepupOnly /collectionName:"Fabrikam Web Site"  
```  
  
 Pour trouver jusqu'à 50 fichiers dont la taille est supérieure à 10 Ko :  
  
```  
TFSConfig CodeIndex /listLargeFiles /fileCount:50 /minSize:10 /collectionName:"Fabrikam Web Site"  
```  
  
 Pour exclure un fichier spécifique de l'indexation et l'ajouter à la liste des fichiers ignorés :  
  
```  
TFSConfig CodeIndex /ignoreList:add "$/Fabrikam Web Site/Catalog.cs" /collectionName:"Fabrikam Web Site"  
```  
  
 Pour afficher tous les fichiers qui ne sont pas indexés :  
  
```  
TFSConfig CodeIndex /ignoreList:view  
```  
  
 Pour effacer les données précédemment indexées et redémarrer l'indexation :  
  
```  
TFSConfig CodeIndex /reindexAll /collectionName:"Fabrikam Web Site"  
```  
  
 Pour enregistrer la totalité de l'historique des ensembles de modifications :  
  
```  
TFSConfig CodeIndex /indexHistoryPeriod:all /collectionName:"Fabrikam Web Site"  
```  
  
 Pour supprimer la limite de taille sur les données temporaire CodeLens et poursuivre l'indexation indépendamment de la taille des données temporaires :  
  
```  
TFSConfig CodeIndex /temporaryDataSizeLimit:disable /collectionName:"Fabrikam Web Site"  
```  
  
 Pour supprimer l'index de code avec confirmation :  
  
```  
TFSConfig CodeIndex /destroyCodeIndex /collectionName:"Fabrikam Web Site"  
```  
  
## <a name="see-also"></a>Voir aussi

[Rechercher les modifications de code et d’autres historiques avec CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md)  
[Gestion de la configuration du serveur avec TFSConfig](http://msdn.microsoft.com/en-us/94424190-3b6b-4f33-a6b6-5807f4225b62)  
[Outils de ligne de commande pour TFS](http://msdn.microsoft.com/en-us/be8c997a-b97b-4e59-97f5-04db0a601a6c)