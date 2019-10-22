---
title: Interface IActiveScriptAuthor | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: ed0734fa48d58a5eae779c75c838c09215ed60a0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576157"
---
# <a name="iactivescriptauthor-interface"></a>IActiveScriptAuthor, interface
Représente les services de création, notamment IntelliSense et le classement des informations.  
  
 En plus des méthodes héritées de `IUnknown`, l’interface `IActiveScriptAuthor` expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)|Ajoute le nom d’un élément de niveau racine à l’espace de noms du moteur de création de script. Un *élément de niveau racine* est un objet qui peut contenir des propriétés et des méthodes, et qui peut également contenir une source d’événement.|  
|[IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)|Ajoute un scriptlet de code en tant qu’enfant du niveau racine `IScriptNode` objet. Dans l’hôte, le nom qualifié complet du scriptlet ne peut avoir que deux niveaux.|  
|[IActiveScriptAuthor::AddTypeLib](../../winscript/reference/iactivescriptauthor-addtypelib.md)|Ajoute une bibliothèque de types à l’espace de noms pour le script.|  
|[IActiveScriptAuthor::GetChars](../../winscript/reference/iactivescriptauthor-getchars.md)|Retourne le jeu de caractères de saisie semi-automatique pour un contexte de saisie semi-automatique demandé.|  
|[IActiveScriptAuthor::GetEventHandler](../../winscript/reference/iactivescriptauthor-geteventhandler.md)|Retourne le scriptlet qui a les attributs spécifiés.|  
|[IActiveScriptAuthor::GetInfoFromContext](../../winscript/reference/iactivescriptauthor-getinfofromcontext.md)|Retourne des informations de type et des positions d’ancrage pour un caractère donné dans un bloc de code. Il fournit des informations sur IntelliSense, les listes globales et les conseils sur les paramètres de membre.|  
|[IActiveScriptAuthor::GetLanguageFlags](../../winscript/reference/iactivescriptauthor-getlanguageflags.md)|Retourne des informations sur la langue.|  
|[IActiveScriptAuthor::GetRoot](../../winscript/reference/iactivescriptauthor-getroot.md)|Retourne la racine `IScriptNode` de l’arborescence de script de l’auteur.|  
|[IActiveScriptAuthor::GetScriptletTextAttributes](../../winscript/reference/iactivescriptauthor-getscriptlettextattributes.md)|Retourne les attributs de texte d’un scriptlet.|  
|[IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)|Retourne les attributs de texte d’un bloc de script.|  
|[IActiveScriptAuthor::IsCommitChar](../../winscript/reference/iactivescriptauthor-iscommitchar.md)|Retourne une valeur qui indique si un caractère donné doit valider la saisie semi-automatique des instructions par l’application.|  
|[IActiveScriptAuthor::ParseScriptText](../../winscript/reference/iactivescriptauthor-parsescripttext.md)|Analyse le texte du script, ajoute le texte au moteur de création de script de création et crée un objet `IScriptEntry` qui correspond au bloc de script.|  
|[IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)|Supprime un objet `NamedItem` de l’espace de noms du moteur de création de script.|  
|[IActiveScriptAuthor::RemoveTypeLib](../../winscript/reference/iactivescriptauthor-removetypelib.md)|Supprime une bibliothèque de types de l’espace de noms du moteur de création de script.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de création de scripts actifs](../../winscript/reference/active-script-authoring-interfaces.md)