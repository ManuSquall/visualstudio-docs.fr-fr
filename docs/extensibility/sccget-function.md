---
title: "SccGet (fonction) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccGet"
helpviewer_keywords: 
  - "SccGet (fonction)"
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# SccGet (fonction)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette fonction extrait une copie d'un ou plusieurs fichiers pour l'affichage et la compilation, mais ne pas pour modification. Dans la plupart des systèmes, les fichiers sont marqués comme étant en lecture seule.  
  
## Syntaxe  
  
```cpp#  
SCCRTN SccGet(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### Paramètres  
 pvContext  
 \[in\] La structure de contexte de plug\-in du contrôle de code source.  
  
 hWnd  
 \[in\] Handle vers la fenêtre de l'IDE que le plug\-in de contrôle de code source peut utiliser en tant que parent pour toutes les boîtes de dialogue qu'il fournit.  
  
 nFiles  
 \[in\] Nombre de fichiers spécifié dans le `lpFileNames` tableau.  
  
 lpFileNames  
 \[in\] Tableau des noms complets des fichiers à récupérer.  
  
 Options  
 \[in\] Indicateurs de commande \(`SCC_GET_ALL`, `SCC_GET_RECURSIVE`\).  
  
 pvOptions  
 \[in\] Options spécifiques au plug\-in de contrôle source.  
  
## Valeur de retour  
 L'implémentation de plug\-in de contrôle de source de cette fonction est censée renvoyer une des valeurs suivantes :  
  
|Valeur|Description|  
|------------|-----------------|  
|SCC\_OK|Succès de l'opération d'obtention.|  
|SCC\_E\_FILENOTCONTROLLED|Le fichier n'est pas sous contrôle de code source.|  
|SCC\_E\_OPNOTSUPPORTED|Le système de contrôle de code source ne prend pas en charge cette opération.|  
|SCC\_E\_FILEISCHECKEDOUT|Impossible d'obtenir le fichier que l'utilisateur a extrait.|  
|SCC\_E\_ACCESSFAILURE|Impossible d'accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention. Une nouvelle tentative est recommandée.|  
|SCC\_E\_NOSPECIFIEDVERSION|Version non valide ou date\/heure spécifié.|  
|SCC\_E\_NONSPECIFICERROR|Erreur non spécifique ; fichier n'a pas été synchronisé.|  
|SCC\_I\_OPERATIONCANCELED|Opération annulée avant la fin.|  
|SCC\_E\_NOTAUTHORIZED|L'utilisateur n'est pas autorisé à effectuer cette opération.|  
  
## Notes  
 Cette fonction est appelée avec un nombre et un tableau de noms de fichiers à récupérer. Si l'IDE passe l'indicateur `SCC_GET_ALL`, cela signifie que les éléments `lpFileNames` ne sont pas des fichiers, mais les répertoires, et que tous les fichiers sous contrôle de code source dans les répertoires donnés doivent être récupérés.  
  
 Le `SCC_GET_ALL` indicateur peut être combiné avec le `SCC_GET_RECURSIVE` indicateur pour récupérer tous les fichiers dans les répertoires donnés et tous les sous\-répertoires.  
  
> [!NOTE]
>  `SCC_GET_RECURSIVE` ne doit jamais être transmis sans `SCC_GET_ALL`. Notez également que si les répertoires C:\\A et C:\\A\\B sont tous deux transmis sur une récursive, C:\\A\\B et tous ses sous\-répertoires seront réellement récupérés deux fois. Il incombe de l'IDE, et pas la source de contrôle du plug\-in, pour vous assurer que les doublons tel restent hors du tableau.  
  
 Enfin, même si le contrôle du code source du plug\-in spécifié le `SCC_CAP_GET_NOUI` indicateur lors de l'initialisation, indiquant qu'il n'a pas une interface utilisateur pour une commande Get, cette fonction peut toujours être appelée par l'IDE pour récupérer des fichiers. L'indicateur signifie simplement que l'IDE n'affiche pas un élément de menu Get et que le plug\-in n'est pas prévu fournir l'interface utilisateur.  
  
## Renommer et SccGet  
 Situation : un utilisateur extrait un fichier, par exemple, a.txt et le modifie. Avant a.txt peut être archivé, un second utilisateur renomme le fichier a.txt en b.txt dans la base de données de contrôle de code source, extrait b.txt, effectue quelques modifications au fichier et recherche le fichier. Le premier utilisateur souhaite que les modifications apportées par le second utilisateur afin que le premier utilisateur renomme b.txt leur version locale du fichier a.txt et est une opération get sur le fichier. Toutefois, le cache local qui effectue le suivi des numéros de version considère toujours que la première version d'un fichier a.txt est stockée localement et par conséquent, contrôle de code source ne peut pas résoudre les différences.  
  
 Il existe deux manières de résoudre cette situation où le cache local de versions de contrôle de code source est désynchronisé avec la base de données de contrôle de code source :  
  
1.  N'autorisez pas la modification du nom d'un fichier dans la base de données de contrôle de source qui est actuellement extrait.  
  
2.  Effectuer l'équivalent de « supprimer ancien » suivie de « Ajouter ». L'algorithme suivant est une façon d'y parvenir.  
  
    1.  Appelez le [SccQueryChanges](../extensibility/sccquerychanges-function.md) fonction pour en savoir plus sur le changement de nom d'un fichier a.txt en b.txt dans la base de données de contrôle de code source.  
  
    2.  Renommez le fichier a.txt local b.txt.  
  
    3.  Appelez le `SccGet` fonction a.txt et b.txt.  
  
    4.  Étant donné que le fichier a.txt n'existe pas dans la base de données de contrôle de code source, le cache de la version locale est purgé les informations de version a.txt manquant.  
  
    5.  Le fichier b.txt en cours d'extraction est fusionné avec le contenu du fichier b.txt local.  
  
    6.  Le fichier de mise à jour b.txt peut désormais être archivé.  
  
## Voir aussi  
 [Fonctions d'API de plug\-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [Indicateurs de bits utilisés par des commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md)