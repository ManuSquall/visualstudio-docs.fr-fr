---
title: Interface IActiveScriptAuthor | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptAuthor interface
ms.assetid: df1f454d-01ee-4beb-928b-48513d07365a
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bd9d9c2a330ee72c6a843cd42586a09bb1d51e3c
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346369"
---
# <a name="iactivescriptauthor-interface"></a>IActiveScriptAuthor, interface
Représente la création de services, notamment IntelliSense et le classement des informations.  
  
 Outre les méthodes héritées de `IUnknown`, le `IActiveScriptAuthor` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)|Ajoute le nom d’un élément de niveau racine pour la création d’espace de noms du moteur de script. Un *élément de niveau racine* est un objet qui peut contenir des méthodes et propriétés, et qui peut également contenir une source d’événement.|  
|[IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)|Ajoute un scriptlet de code en tant qu’enfant du niveau racine `IScriptNode` objet. Dans l’hôte, le nom qualifié complet du scriptlet peut avoir uniquement deux niveaux.|  
|[IActiveScriptAuthor::AddTypeLib](../../winscript/reference/iactivescriptauthor-addtypelib.md)|Ajoute une bibliothèque de types à l’espace de noms pour le script.|  
|[IActiveScriptAuthor::GetChars](../../winscript/reference/iactivescriptauthor-getchars.md)|Retourne le jeu de caractères de saisie semi-automatique pour un contexte d’exécution demandée.|  
|[IActiveScriptAuthor::GetEventHandler](../../winscript/reference/iactivescriptauthor-geteventhandler.md)|Retourne le scriptlet qui possède les attributs spécifiés.|  
|[IActiveScriptAuthor::GetInfoFromContext](../../winscript/reference/iactivescriptauthor-getinfofromcontext.md)|Retourne type d’informations et les positions d’ancrage pour un caractère donné dans un bloc de code. Fournit des informations de membre IntelliSense, des listes globales et des conseils sur les paramètres.|  
|[IActiveScriptAuthor::GetLanguageFlags](../../winscript/reference/iactivescriptauthor-getlanguageflags.md)|Retourne des informations de langue.|  
|[IActiveScriptAuthor::GetRoot](../../winscript/reference/iactivescriptauthor-getroot.md)|Retourne le `IScriptNode` racine d’arborescence de script de l’auteur.|  
|[IActiveScriptAuthor::GetScriptletTextAttributes](../../winscript/reference/iactivescriptauthor-getscriptlettextattributes.md)|Retourne les attributs de texte d’un scriptlet.|  
|[IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)|Retourne les attributs de texte d’un bloc de script.|  
|[IActiveScriptAuthor::IsCommitChar](../../winscript/reference/iactivescriptauthor-iscommitchar.md)|Retourne une valeur qui indique si un caractère donné doit valider une saisie semi-automatique des instructions par l’application.|  
|[IActiveScriptAuthor::ParseScriptText](../../winscript/reference/iactivescriptauthor-parsescripttext.md)|Analyse le texte du script, ajoute le texte dans le script de création du moteur de création et crée un `IScriptEntry` objet qui correspond au bloc de script.|  
|[IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)|Supprime un `NamedItem` objet à partir de l’espace de noms du script du moteur de création.|  
|[IActiveScriptAuthor::RemoveTypeLib](../../winscript/reference/iactivescriptauthor-removetypelib.md)|Supprime une bibliothèque de types à partir de l’espace de noms du moteur de création de script.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de création de scripts actifs](../../winscript/reference/active-script-authoring-interfaces.md)