---
title: Codes d’erreur | Microsoft Docs
description: Cet article contient la liste des codes d’erreur, des valeurs et des descriptions pour les fonctions d’API de plug-in de contrôle de code source.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- error codes, source control plug-ins
- source control plug-ins, error codes
- errors [Visual Studio SDK]
ms.assetid: d9cbd1c4-719b-467a-8100-333c1e146d3b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: eedc9311bcafdd4241e065b40079abed3977dcef
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898303"
---
# <a name="error-codes"></a>Codes d’erreur
Lorsqu’une fonction d’API de plug-in de contrôle de code source retourne une erreur, il doit s’agir de l’un des codes d’erreur suivants. Toutes les erreurs sont négatives, les avertissements ou les codes d’erreur d’information sont positifs et la réussite est 0.

|Code d'erreur|Valeur|Description|
|----------------|-----------|-----------------|
|`SCC_I_SHARESUBPROJOK`|7|Le plug-in prend en charge l’ajout de fichiers du contrôle de code source en deux étapes. Pour plus d’informations, consultez [SccSetOption](../extensibility/sccsetoption-function.md).|
|`SCC_I_FILEDIFFERS`|6|Le fichier local est différent du fichier dans la base de données de contrôle de code source (par exemple, [SccDiff](../extensibility/sccdiff-function.md) peut retourner cette valeur).|
|`SCC_I_RELOADFILE`|5|Le fichier local a été modifié pendant l’opération de contrôle de code source ; l’IDE doit recharger le fichier si possible.|
|`SCC_I_FILENOTAFFECTED`|4|Le fichier n’est pas affecté.|
|`SCC_I_PROJECTCREATED`|3|Le projet a été créé pendant l’opération de contrôle de code source (par exemple, lors d’un appel à [SccOpenProject](../extensibility/sccopenproject-function.md) lorsque l' `SCC_OP_CREATEIFNEW` indicateur est spécifié).|
|`SCC_I_OPERATIONCANCELED`|2|L'opération a été annulée.|
|`SCC_I_ADV_SUPPORT`|1|Le plug-in prend en charge les options avancées pour la commande spécifiée. Pour plus d’informations, consultez [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md).|
|`SCC_OK`|0|Réussite.|
|`SCC_E_INITIALIZEFAILED`|-1|Erreur : échec de l’initialisation.|
|`SCC_E_UNKNOWNPROJECT`|-2|Erreur : le projet est inconnu.|
|`SCC_E_COULDNOTCREATEPROJECT`|-3|Erreur : impossible de créer le projet.|
|`SCC_E_NOTCHECKEDOUT`|-4|Erreur : le fichier n’est pas extrait.|
|`SCC_E_ALREADYCHECKEDOUT`|-5|Erreur : le fichier est déjà extrait.|
|`SCC_E_FILEISLOCKED`|-6|Erreur : le fichier est verrouillé.|
|`SCC_E_FILEOUTEXCLUSIVE`|-7|Erreur : le fichier est extrait en mode exclusif.|
|`SCC_E_ACCESSFAILURE`|-8|Un problème est survenu lors de l’accès au système de contrôle de code source, probablement en raison de problèmes de réseau ou de contention. Une nouvelle tentative est recommandée.|
|`SCC_E_CHECKINCONFLICT`|-9|Erreur : un conflit s’est produite lors de l’archivage.|
|`SCC_E_FILEALREADYEXISTS`|-10|Erreur : le fichier existe déjà.|
|`SCC_E_FILENOTCONTROLLED`|-11|Erreur : le fichier n’est pas sous contrôle de code source.|
|`SCC_E_FILEISCHECKEDOUT`|12|Erreur : le fichier est extrait.|
|`SCC_E_NOSPECIFIEDVERSION`|-13|Erreur : il n’existe aucune version spécifiée.|
|`SCC_E_OPNOTSUPPORTED`|-14|Erreur : l’opération n’est pas prise en charge.|
|`SCC_E_NONSPECIFICERROR`|-15.0|Erreur non spécifique.|
|`SCC_E_OPNOTPERFORMED`|-16|Erreur, l’opération n’a pas été effectuée.|
|`SCC_E_TYPENOTSUPPORTED`|-17|Erreur : le type du fichier, par exemple, binaire, n’est pas pris en charge par le système de contrôle de code source.|
|`SCC_E_VERIFYMERGE`|-18|Le fichier a été fusionné automatiquement mais n’a pas été vérifié, car il est en attente de vérification par l’utilisateur.|
|`SCC_E_FIXMERGE`|-19|Le fichier a été fusionné automatiquement mais n’a pas été archivé en raison d’un conflit de fusion qui doit être résolu manuellement.|
|`SCC_E_SHELLFAILURE`|-20|Erreur en raison d’un échec de l’interpréteur de commandes.|
|`SCC_E_INVALIDUSER`|-21|Erreur : l’utilisateur n’est pas valide.|
|`SCC_E_PROJECTALREADYOPEN`|-22|Erreur : le projet est déjà ouvert.|
|`SCC_E_PROJSYNTAXERR`|-23|Erreur de syntaxe du projet.|
|`SCC_E_INVALIDFILEPATH`|-24|Erreur : le chemin d’accès au fichier n’est pas valide.|
|`SCC_E_PROJNOTOPEN`|-25|Erreur : le projet n’est pas ouvert.|
|`SCC_E_NOTAUTHORIZED`|-26|Erreur : l’utilisateur n’est pas autorisé à effectuer cette opération.|
|`SCC_E_FILESYNTAXERR`|-27|Erreur de syntaxe de fichier.|
|`SCC_E_FILENOTEXIST`|28|Erreur, le fichier local n’existe pas.|
|`SCC_E_CONNECTIONFAILURE`|-29|Erreur : un échec de connexion s’est produite.|
|`SCC_E_UNKNOWNERROR`|-30|Erreur inconnue.|
|`SCC_E_BACKGROUNDGETINPROGRESS`|-31|L’opération de récupération en arrière-plan est actuellement en cours.|

## <a name="macros-provided-for-quick-checking"></a>Macros fournies pour la vérification rapide

```cpp
IS_SCC_ERROR(rtn) (((rtn) < 0) ? TRUE : FALSE)
IS_SCC_SUCCESS(rtn) (((rtn) == SCC_OK) ? TRUE : FALSE)
IS_SCC_WARNING(rtn) (((rtn) > 0) ? TRUE : FALSE)
```

## <a name="remarks"></a>Remarques
 Toutes les fonctions API de plug-in de contrôle de code source (à l’exception de [SccAdd](../extensibility/sccadd-function.md), [SccCheckin](../extensibility/scccheckin-function.md)et [SccDiff](../extensibility/sccdiff-function.md)) sont supposées réussies lorsque les fichiers locaux qui sont passés comme arguments n’existent pas dans le dossier de travail. Par exemple, l’IDE peut émettre un appel à [SccCheckout](../extensibility/scccheckout-function.md) ou [SccUncheckout](../extensibility/sccuncheckout-function.md) sur un fichier qui n’existe pas dans le dossier de travail, mais qui existe dans le système de contrôle de code source. Cet appel a échoué. La fonction devrait échouer uniquement lorsqu’il n’y a aucun fichier dans le dossier de travail ou dans le système de contrôle de code source.

 Certaines fonctions, telles que `SccAdd` et `SccCheckin` , doivent retourner spécifiquement `SCC_E_FILENOTEXIST` lorsque le fichier du dossier de travail n’existe pas. D’autres fonctions sont supposées parvenir lorsque le fichier de travail n’existe pas, si les fonctions fonctionnent sur un nom de fichier valide dans le système de contrôle de code source.

 Le plug-in de contrôle de code source ne doit pas faire d’hypothèses concernant les privilèges sur un fichier dans le dossier de travail, même si le plug-in avait marqué le fichier en lecture seule lors d’une opération. Vous pouvez déplacer, supprimer et modifier un fichier dans le dossier de travail en dehors du contrôle du plug-in.

## <a name="see-also"></a>Voir aussi
- [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)
