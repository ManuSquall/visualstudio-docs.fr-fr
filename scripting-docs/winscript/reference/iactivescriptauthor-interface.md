---
title: IActiveScriptAuthor (Interface) | Documents Microsoft
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
ms.openlocfilehash: 37abb356ab24d64a05a1f1209809d63e2f55e228
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24645769"
---
# <a name="iactivescriptauthor-interface"></a>IActiveScriptAuthor, interface
Représente la création de services, notamment IntelliSense et le classement des informations.  
  
 Outre les méthodes héritées de `IUnknown`, le `IActiveScriptAuthor` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)|Ajoute le nom d’un élément de niveau racine pour l’espace de noms du moteur de création de script. A *élément de niveau racine* est un objet qui peut contenir des propriétés et méthodes, et qui peut également contenir une source d’événement.|  
|[IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)|Ajoute un scriptlet code en tant qu’enfant du niveau racine `IScriptNode` objet. Dans l’hôte, le nom qualifié complet du scriptlet peut avoir deux niveaux.|  
|[IActiveScriptAuthor::AddTypeLib](../../winscript/reference/iactivescriptauthor-addtypelib.md)|Ajoute une bibliothèque de types à l’espace de noms pour le script.|  
|[IActiveScriptAuthor::GetChars](../../winscript/reference/iactivescriptauthor-getchars.md)|Retourne le jeu de caractères de fin pour un contexte d’exécution demandé.|  
|[IActiveScriptAuthor::GetEventHandler](../../winscript/reference/iactivescriptauthor-geteventhandler.md)|Retourne le scriptlet qui possède les attributs spécifiés.|  
|[IActiveScriptAuthor::GetInfoFromContext](../../winscript/reference/iactivescriptauthor-getinfofromcontext.md)|Retourne de type d’informations et les positions d’ancrage d’un caractère donné dans un bloc de code. Fournit des informations de membre IntelliSense, des listes globales et des conseils sur les paramètres.|  
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