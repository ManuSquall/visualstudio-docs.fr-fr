---
title: "Codes d&#39;erreur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "codes d'erreur, plug-ins de contrôle de code source"
  - "source contrôle plug-ins, les codes d'erreur"
  - "erreurs (Visual Studio SDK)"
ms.assetid: d9cbd1c4-719b-467a-8100-333c1e146d3b
caps.latest.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 19
---
# Codes d&#39;erreur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Lorsqu'une fonction API de plug\-in de contrôle de code Source retourne une erreur, il est supposé être un des codes d'erreur suivants. Toutes les erreurs sont négatives, les avertissements ou les codes d'erreur d'information sont positives, et la réussite est 0.  
  
|Code d'erreur|Valeur|Description|  
|-------------------|------------|-----------------|  
|`SCC_I_SHARESUBPROJOK`|7|Plug\-in prend en charge l'ajout de fichiers à partir du contrôle de code source en deux étapes. Pour plus d'informations, consultez [SccSetOption](../extensibility/sccsetoption-function.md).|  
|`SCC_I_FILEDIFFERS`|6|Le fichier local est différent du fichier dans la base de données de contrôle de code source \(par exemple, [SccDiff](../extensibility/sccdiff-function.md) peut retourner cette valeur\).|  
|`SCC_I_RELOADFILE`|5|Fichier local ont été modifié pendant l'opération de contrôle de code source ; l'IDE doit recharger le fichier si possible.|  
|`SCC_I_FILENOTAFFECTED`|4|Le fichier n'est pas affecté.|  
|`SCC_I_PROJECTCREATED`|3|Le projet a été créé pendant l'opération de contrôle de code source \(par exemple, pendant un appel à [SccOpenProject](../extensibility/sccopenproject-function.md) lorsque `SCC_OP_CREATEIFNEW` indicateur est spécifié\).|  
|`SCC_I_OPERATIONCANCELED`|2|Opération annulée.|  
|`SCC_I_ADV_SUPPORT`|1|Plug\-in prend en charge des options avancées pour la commande spécifiée. Pour plus d'informations, consultez [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md).|  
|`SCC_OK`|0|Opération réussie.|  
|`SCC_E_INITIALIZEFAILED`|\-1|Erreur : Échec de l'initialisation.|  
|`SCC_E_UNKNOWNPROJECT`|\-2|Erreur : le projet est inconnu.|  
|`SCC_E_COULDNOTCREATEPROJECT`|\-3|Erreur : le projet n'a pas pu être créé.|  
|`SCC_E_NOTCHECKEDOUT`|\-4|Erreur : le fichier n'est pas extrait.|  
|`SCC_E_ALREADYCHECKEDOUT`|\-5|Erreur : le fichier est déjà extrait.|  
|`SCC_E_FILEISLOCKED`|\-6|Erreur : le fichier est verrouillé.|  
|`SCC_E_FILEOUTEXCLUSIVE`|\-7|Erreur : le fichier est extrait en mode exclusif.|  
|`SCC_E_ACCESSFAILURE`|\-8|Impossible d'accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention. Une nouvelle tentative est recommandée.|  
|`SCC_E_CHECKINCONFLICT`|\-9|Erreur : il existait un conflit au cours de l'archivage.|  
|`SCC_E_FILEALREADYEXISTS`|\-10|Erreur : le fichier existe déjà.|  
|`SCC_E_FILENOTCONTROLLED`|\-11|Erreur : le fichier n'est pas sous contrôle de code source.|  
|`SCC_E_FILEISCHECKEDOUT`|\-12|Erreur : le fichier est extrait.|  
|`SCC_E_NOSPECIFIEDVERSION`|\-13|Erreur : il n'existe aucune version spécifiée.|  
|`SCC_E_OPNOTSUPPORTED`|\-14|Erreur : l'opération n'est pas pris en charge.|  
|`SCC_E_NONSPECIFICERROR`|\-15|Erreur non spécifique.|  
|`SCC_E_OPNOTPERFORMED`|\-16|Erreur, l'opération n'a pas été effectuée.|  
|`SCC_E_TYPENOTSUPPORTED`|\-17|Erreur : le type de fichier, par exemple, binaire, n'est pas pris en charge par le système de contrôle de code source.|  
|`SCC_E_VERIFYMERGE`|\-18|Fichier a été fusionnée automatiquement, mais n'a pas été activée car il s'agit de vérification de l'utilisateur en attente.|  
|`SCC_E_FIXMERGE`|\-19|Fichier a été fusionnée automatiquement, mais n'a pas été archivé en raison d'un conflit de fusion qui doit être résolu manuellement.|  
|`SCC_E_SHELLFAILURE`|\-20|Erreur due à un échec de l'interpréteur de commandes.|  
|`SCC_E_INVALIDUSER`|\-21|Erreur : l'utilisateur n'est pas valide.|  
|`SCC_E_PROJECTALREADYOPEN`|\-22|Erreur : le projet est déjà ouvert.|  
|`SCC_E_PROJSYNTAXERR`|\-23|Erreur de syntaxe du projet.|  
|`SCC_E_INVALIDFILEPATH`|\-24|Erreur : le chemin d'accès n'est pas valide.|  
|`SCC_E_PROJNOTOPEN`|\-25|Erreur : le projet n'est pas ouvert.|  
|`SCC_E_NOTAUTHORIZED`|\-26|Erreur : l'utilisateur n'est pas autorisé à effectuer cette opération.|  
|`SCC_E_FILESYNTAXERR`|\-27|Erreur de syntaxe du fichier.|  
|`SCC_E_FILENOTEXIST`|\-28|Erreur, le fichier local n'existe pas.|  
|`SCC_E_CONNECTIONFAILURE`|\-29|Erreur : Échec de la connexion est survenu.|  
|`SCC_E_UNKNOWNERROR`|\-30|Erreur inconnue.|  
|`SCC_E_BACKGROUNDGETINPROGRESS`|\-31|Opération d'extraction en arrière\-plan en cours.|  
  
## Macros fournis pour vérification rapide  
  
```cpp#  
IS_SCC_ERROR(rtn) (((rtn) < 0) ? TRUE : FALSE) IS_SCC_SUCCESS(rtn) (((rtn) == SCC_OK) ? TRUE : FALSE) IS_SCC_WARNING(rtn) (((rtn) > 0) ? TRUE : FALSE)  
```  
  
## Remarques  
 Toutes les fonctions API de plug\-in de contrôle de code Source \(sauf le [SccAdd](../extensibility/sccadd-function.md), [SccCheckin](../extensibility/scccheckin-function.md), et [SccDiff](../extensibility/sccdiff-function.md)\) réussissent lorsque les fichiers locaux qui sont passés comme arguments n'existent pas dans le dossier de travail. Par exemple, l'IDE peut émettre un appel à la [SccCheckout](../extensibility/scccheckout-function.md) ou [SccUncheckout](../extensibility/sccuncheckout-function.md) sur un fichier qui n'existe pas dans le dossier de travail, mais il existe dans le système de contrôle de code source. Cet appel réussit. Uniquement lorsqu'il n'existe aucun fichier dans le dossier de travail ou dans le système de contrôle de source est la fonction va échouer.  
  
 Certaines fonctions, telles que `SccAdd` et `SccCheckin`, doit retourner spécifiquement `SCC_E_FILENOTEXIST` lorsque le fichier dans le dossier de travail n'existe pas. Autres fonctions doivent réussir lorsque le fichier de travail n'existe pas, si les fonctions fonctionnent sur un nom de fichier valide dans le système de contrôle de code source.  
  
 Le plug\-in de contrôle de code source doit pas faire d'hypothèses concernant les privilèges sur un fichier dans le dossier de travail, même si le plug\-in a marqué le fichier en lecture seule pendant une opération. Un fichier dans le dossier de travail peut être déplacé, supprimé et modifié à l'extérieur de contrôle du plug\-in.  
  
## Voir aussi  
 [Plug\-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)