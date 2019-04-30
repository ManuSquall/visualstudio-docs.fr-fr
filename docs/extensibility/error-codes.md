---
title: Codes d’erreur | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- error codes, source control plug-ins
- source control plug-ins, error codes
- errors [Visual Studio SDK]
ms.assetid: d9cbd1c4-719b-467a-8100-333c1e146d3b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2e3dc26b8dd2e17e201cf760db68d0faf7e231ed
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62863965"
---
# <a name="error-codes"></a>Codes d’erreur
Lorsqu’une fonction de l’API de plug-in de contrôle de Source renvoie une erreur, il est censé être un des codes d’erreur suivants. Toutes les erreurs sont négatifs, avertissements ou des codes d’erreur d’information sont positives, et de réussite est 0.

|Code d'erreur|Value|Description|
|----------------|-----------|-----------------|
|`SCC_I_SHARESUBPROJOK`|7|Plug-in prend en charge l’ajout de fichiers de contrôle de code source en deux étapes. Pour plus d’informations, consultez [SccSetOption](../extensibility/sccsetoption-function.md).|
|`SCC_I_FILEDIFFERS`|6|Le fichier local est différent du fichier dans la base de données de contrôle de code source (par exemple, [SccDiff](../extensibility/sccdiff-function.md) peut retourner cette valeur).|
|`SCC_I_RELOADFILE`|5|Fichier local a été modifié pendant l’opération de contrôle de code source ; l’IDE doit recharger le fichier si possible.|
|`SCC_I_FILENOTAFFECTED`|4|Le fichier n’est pas affecté.|
|`SCC_I_PROJECTCREATED`|3|Le projet a été créé pendant l’opération de contrôle de code source (par exemple, pendant un appel à [SccOpenProject](../extensibility/sccopenproject-function.md) lorsque `SCC_OP_CREATEIFNEW` indicateur est spécifié).|
|`SCC_I_OPERATIONCANCELED`|2|Opération a été annulée.|
|`SCC_I_ADV_SUPPORT`|1|Plug-in prend en charge des options avancées pour la commande spécifiée. Pour plus d’informations, consultez [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md).|
|`SCC_OK`|0|Opération réussie.|
|`SCC_E_INITIALIZEFAILED`|-1|Erreur : Échec de l’initialisation.|
|`SCC_E_UNKNOWNPROJECT`|-2|Erreur : le projet est inconnu.|
|`SCC_E_COULDNOTCREATEPROJECT`|-3|Erreur : le projet n’a pas pu être créé.|
|`SCC_E_NOTCHECKEDOUT`|-4|Erreur : le fichier n'est pas extrait.|
|`SCC_E_ALREADYCHECKEDOUT`|-5|Erreur : le fichier est déjà extrait.|
|`SCC_E_FILEISLOCKED`|-6|Erreur : le fichier est verrouillé.|
|`SCC_E_FILEOUTEXCLUSIVE`|-7|Erreur : le fichier est extrait en mode exclusif.|
|`SCC_E_ACCESSFAILURE`|-8|Impossible d’accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention. Une nouvelle tentative est recommandée.|
|`SCC_E_CHECKINCONFLICT`|-9|Erreur : s’est un conflit au cours de l’archivage.|
|`SCC_E_FILEALREADYEXISTS`|-10|Erreur : le fichier existe déjà.|
|`SCC_E_FILENOTCONTROLLED`|-11|Erreur : le fichier n’est pas sous contrôle de code source.|
|`SCC_E_FILEISCHECKEDOUT`|-12|Erreur : le fichier est extrait.|
|`SCC_E_NOSPECIFIEDVERSION`|-13|Erreur : il n’existe aucune version spécifiée.|
|`SCC_E_OPNOTSUPPORTED`|-14|Erreur : l’opération n’est pas pris en charge.|
|`SCC_E_NONSPECIFICERROR`|-15|Erreur non spécifique.|
|`SCC_E_OPNOTPERFORMED`|-16|Erreur, l’opération n’a pas été effectuée.|
|`SCC_E_TYPENOTSUPPORTED`|-17|Erreur : le type du fichier, par exemple, binaire, n’est pas pris en charge par le système de contrôle de code source.|
|`SCC_E_VERIFYMERGE`|-18|Fichier a été fusionnée automatique mais n’a pas été vérifiée, car il est la vérification de l’utilisateur en attente.|
|`SCC_E_FIXMERGE`|-19|Fichier a été fusionnée automatique mais n’a pas été archivé en raison d’un conflit de fusion qui doit être résolu manuellement.|
|`SCC_E_SHELLFAILURE`|-20|Erreur due à une défaillance de l’interpréteur de commandes.|
|`SCC_E_INVALIDUSER`|-21|Erreur : l’utilisateur n’est pas valide.|
|`SCC_E_PROJECTALREADYOPEN`|-22|Erreur : le projet est déjà ouvert.|
|`SCC_E_PROJSYNTAXERR`|-23|Erreur de syntaxe du projet.|
|`SCC_E_INVALIDFILEPATH`|-24|Erreur : le chemin d’accès de fichier n’est pas valide.|
|`SCC_E_PROJNOTOPEN`|-25|Erreur : le projet n’est pas ouvert.|
|`SCC_E_NOTAUTHORIZED`|-26|Erreur : l’utilisateur n’est pas autorisé à effectuer cette opération.|
|`SCC_E_FILESYNTAXERR`|-27|Erreur de syntaxe de fichier.|
|`SCC_E_FILENOTEXIST`|-28|Erreur, le fichier local n’existe pas.|
|`SCC_E_CONNECTIONFAILURE`|-29|Erreur : Échec de la connexion est survenu.|
|`SCC_E_UNKNOWNERROR`|-30|Erreur inconnue.|
|`SCC_E_BACKGROUNDGETINPROGRESS`|-31|Opération d’obtention d’arrière-plan est actuellement en cours.|

## <a name="macros-provided-for-quick-checking"></a>Macros fournis pour la vérification rapide

```cpp
IS_SCC_ERROR(rtn) (((rtn) < 0) ? TRUE : FALSE)
IS_SCC_SUCCESS(rtn) (((rtn) == SCC_OK) ? TRUE : FALSE)
IS_SCC_WARNING(rtn) (((rtn) > 0) ? TRUE : FALSE)
```

## <a name="remarks"></a>Notes
 Toutes les fonctions API de plug-in de contrôle de code Source (sauf le [SccAdd](../extensibility/sccadd-function.md), [SccCheckin](../extensibility/scccheckin-function.md), et [SccDiff](../extensibility/sccdiff-function.md)) sont censées aboutir lorsque les fichiers locaux qui sont passés comme arguments effectuez n’existe pas dans le dossier de travail. Par exemple, l’IDE peut émettre un appel à la [SccCheckout](../extensibility/scccheckout-function.md) ou [SccUncheckout](../extensibility/sccuncheckout-function.md) sur un fichier qui n’existe pas dans le dossier de travail, mais qui existe dans le système de contrôle source. Cet appel réussit. Uniquement lorsqu’il n’existe aucun fichier dans le dossier de travail ou dans le système de contrôle de source est la fonction va échouer.

 Certaines fonctions, telles que `SccAdd` et `SccCheckin`, doit retourner spécifiquement `SCC_E_FILENOTEXIST` lorsque le fichier dans le dossier de travail n’existe pas. Autres fonctions sont censées aboutir lorsque le fichier de travail n’existe pas, si les fonctions opèrent sur un nom de fichier valide dans le système de contrôle source.

 Le plug-in de contrôle de code source doit pas faire d’hypothèses concernant les privilèges sur un fichier dans le dossier de travail, même si le plug-in a marqué le fichier en lecture seule pendant une opération. Un fichier dans le dossier de travail peut être déplacé, supprimé et modifié en dehors de contrôle du plug-in.

## <a name="see-also"></a>Voir aussi
- [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)