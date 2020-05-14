---
title: Codes d’erreur (en anglais) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- error codes, source control plug-ins
- source control plug-ins, error codes
- errors [Visual Studio SDK]
ms.assetid: d9cbd1c4-719b-467a-8100-333c1e146d3b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34072f6ddbd632f83dd308c6cb63427e02bb110b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711845"
---
# <a name="error-codes"></a>Codes d’erreur
Lorsqu’une fonction d’API rechargeable de contrôle source renvoie une erreur, on s’attend à ce qu’elle soit l’un des codes d’erreur suivants. Toutes les erreurs sont négatives, les avertissements ou les codes d’erreur d’information sont positifs, et le succès est 0.

|Code d'erreur|Valeur|Description|
|----------------|-----------|-----------------|
|`SCC_I_SHARESUBPROJOK`|7|Plug-in prend en charge l’ajout de fichiers à partir du contrôle source en deux étapes. Pour plus d’informations, voir [SccSetOption](../extensibility/sccsetoption-function.md).|
|`SCC_I_FILEDIFFERS`|6|Le fichier local est différent du fichier dans la base de données de contrôle source (par exemple, [SccDiff](../extensibility/sccdiff-function.md) peut retourner cette valeur).|
|`SCC_I_RELOADFILE`|5|Le fichier local a été modifié pendant l’opération de contrôle source; l’IDE doit recharger le fichier si possible.|
|`SCC_I_FILENOTAFFECTED`|4|Le fichier n’est pas affecté.|
|`SCC_I_PROJECTCREATED`|3|Le projet a été créé lors de l’opération de contrôle à `SCC_OP_CREATEIFNEW` la source (par exemple, lors d’un appel à [SccOpenProject](../extensibility/sccopenproject-function.md) lorsque le drapeau est spécifié).|
|`SCC_I_OPERATIONCANCELED`|2|L'opération a été annulée.|
|`SCC_I_ADV_SUPPORT`|1|Plug-in prend en charge les options avancées pour la commande spécifiée. Pour plus d’informations, voir [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md).|
|`SCC_OK`|0|Réussite.|
|`SCC_E_INITIALIZEFAILED`|-1|Erreur : l’initialisation a échoué.|
|`SCC_E_UNKNOWNPROJECT`|-2|Erreur : le projet est inconnu.|
|`SCC_E_COULDNOTCREATEPROJECT`|-3|Erreur : le projet n’a pas pu être créé.|
|`SCC_E_NOTCHECKEDOUT`|-4|Erreur : le fichier n’est pas vérifié.|
|`SCC_E_ALREADYCHECKEDOUT`|-5|Erreur : le fichier est déjà vérifié.|
|`SCC_E_FILEISLOCKED`|-6|Erreur : le fichier est verrouillé.|
|`SCC_E_FILEOUTEXCLUSIVE`|-7|Erreur : le fichier est exclusivement vérifié.|
|`SCC_E_ACCESSFAILURE`|-8|Il y avait un problème d’accès au système de contrôle à la source, probablement en raison de problèmes de réseau ou de contention. Une nouvelle tentative est recommandée.|
|`SCC_E_CHECKINCONFLICT`|-9|Erreur : il y a eu un conflit lors de l’enregistrement.|
|`SCC_E_FILEALREADYEXISTS`|-10|Erreur : le fichier existe déjà.|
|`SCC_E_FILENOTCONTROLLED`|-11|Erreur : le fichier n’est pas sous contrôle source.|
|`SCC_E_FILEISCHECKEDOUT`|-12|Erreur : le fichier est vérifié.|
|`SCC_E_NOSPECIFIEDVERSION`|-13|Erreur : il n’y a pas de version spécifiée.|
|`SCC_E_OPNOTSUPPORTED`|-14|Erreur : l’opération n’est pas prise en charge.|
|`SCC_E_NONSPECIFICERROR`|-15|Erreur non spécifique.|
|`SCC_E_OPNOTPERFORMED`|-16|Erreur, l’opération n’a pas été effectuée.|
|`SCC_E_TYPENOTSUPPORTED`|-17|Erreur : le type de fichier, par exemple binaire, n’est pas pris en charge par le système de contrôle du code source.|
|`SCC_E_VERIFYMERGE`|-18|Fichier a été auto-fusionné, mais n’a pas été vérifié parce qu’il est en attente de vérification de l’utilisateur.|
|`SCC_E_FIXMERGE`|-19|Le fichier a été auto-fusionné mais n’a pas été enregistré en raison d’un conflit de fusion qui doit être résolu manuellement.|
|`SCC_E_SHELLFAILURE`|-20|Erreur due à une défaillance de la coque.|
|`SCC_E_INVALIDUSER`|-21|Erreur : l’utilisateur est invalide.|
|`SCC_E_PROJECTALREADYOPEN`|-22|Erreur : le projet est déjà ouvert.|
|`SCC_E_PROJSYNTAXERR`|-23|Erreur de syntaxe du projet.|
|`SCC_E_INVALIDFILEPATH`|-24|Erreur : le chemin du fichier est invalide.|
|`SCC_E_PROJNOTOPEN`|-25|Erreur : le projet n’est pas ouvert.|
|`SCC_E_NOTAUTHORIZED`|-26|Erreur : l’utilisateur n’est pas autorisé à effectuer cette opération.|
|`SCC_E_FILESYNTAXERR`|-27|Erreur de syntaxe de fichier.|
|`SCC_E_FILENOTEXIST`|-28|Erreur, le fichier local n’existe pas.|
|`SCC_E_CONNECTIONFAILURE`|-29|Erreur : il y a eu une défaillance de connexion.|
|`SCC_E_UNKNOWNERROR`|-30|Erreur inconnue.|
|`SCC_E_BACKGROUNDGETINPROGRESS`|-31|L’exploitation de fond est actuellement en cours.|

## <a name="macros-provided-for-quick-checking"></a>Macros prévu pour la vérification rapide

```cpp
IS_SCC_ERROR(rtn) (((rtn) < 0) ? TRUE : FALSE)
IS_SCC_SUCCESS(rtn) (((rtn) == SCC_OK) ? TRUE : FALSE)
IS_SCC_WARNING(rtn) (((rtn) > 0) ? TRUE : FALSE)
```

## <a name="remarks"></a>Notes
 Toutes les fonctions d’API de contrôle des sources (à l’exception du [SccAdd](../extensibility/sccadd-function.md), [de SccCheckin](../extensibility/scccheckin-function.md)et [du SccDiff](../extensibility/sccdiff-function.md)) devraient réussir lorsque les fichiers locaux qui sont adoptés comme arguments n’existent pas dans le dossier de travail. Par exemple, l’IDE peut émettre un appel au [SccCheckout](../extensibility/scccheckout-function.md) ou [à la SccUncheckout](../extensibility/sccuncheckout-function.md) sur un fichier qui n’existe pas dans le dossier de travail, mais qui existe dans le système de contrôle source. Cet appel réussirait. Ce n’est que lorsqu’il n’y a pas de fichier dans le dossier de travail ou dans le système de contrôle source que la fonction devrait échouer.

 Certaines fonctions, `SccAdd` telles `SccCheckin`que et `SCC_E_FILENOTEXIST` , doivent revenir spécifiquement lorsque le fichier dans le dossier de travail n’existe pas. D’autres fonctions devraient réussir lorsque le fichier de travail n’existe pas, si les fonctions fonctionnent sur un nom de fichier valide dans le système de contrôle source.

 Le plug-in de contrôle source ne doit pas faire d’hypothèses concernant les privilèges d’un fichier dans le dossier de travail, même si le plug-in avait marqué le fichier lu uniquement lors d’une opération. Un fichier dans le dossier de travail peut être déplacé, supprimé et modifié en dehors du contrôle du plug-in.

## <a name="see-also"></a>Voir aussi
- [Plug-ins de contrôle des sources](../extensibility/source-control-plug-ins.md)
