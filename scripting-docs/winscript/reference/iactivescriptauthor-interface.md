---
title: "IActiveScriptAuthor, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptAuthor (interface)"
ms.assetid: df1f454d-01ee-4beb-928b-48513d07365a
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# IActiveScriptAuthor, interface
Représente des services de création, notamment Intellisense et le classement des informations.  
  
 Outre les méthodes héritées de `IUnknown`, l'interface `IActiveScriptAuthor` expose les méthodes suivantes.  
  
## Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)|Ajoute le nom d'un élément racine à l'espace de noms du moteur de création de script.  *Un élément racine* est un objet qui peut contenir des propriétés et des méthodes, et qui peut également contenir une source d'événement.|  
|[IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)|Ajoute un scriptlet de code comme un enfant de l'objet d' `IScriptNode` de niveau racine.  Dans l'hôte, le nom qualifié complet du scriptlet peut avoir uniquement deux couches.|  
|[IActiveScriptAuthor::AddTypeLib](../../winscript/reference/iactivescriptauthor-addtypelib.md)|Ajoute une bibliothèque de types dans l'espace de noms pour le script.|  
|[IActiveScriptAuthor::GetChars](../../winscript/reference/iactivescriptauthor-getchars.md)|Retourne le jeu de caractères d'achèvement d'un contexte demandé d'achèvement.|  
|[IActiveScriptAuthor::GetEventHandler](../../winscript/reference/iactivescriptauthor-geteventhandler.md)|Retourne le scriptlet qui a les attributs spécifiés.|  
|[IActiveScriptAuthor::GetInfoFromContext](../../winscript/reference/iactivescriptauthor-getinfofromcontext.md)|Retourne les informations de type et positions d'ancrage d'un caractère donné dans un bloc de code.  Cela fournit des informations pour le membre Intellisense, des listes globales, et les conseils de paramètre.|  
|[IActiveScriptAuthor::GetLanguageFlags](../../winscript/reference/iactivescriptauthor-getlanguageflags.md)|Retourne les informations de langage.|  
|[IActiveScriptAuthor::GetRoot](../../winscript/reference/iactivescriptauthor-getroot.md)|Retourne la racine d' `IScriptNode` de l'arborescence du script de l'auteur.|  
|[IActiveScriptAuthor::GetScriptletTextAttributes](../../winscript/reference/iactivescriptauthor-getscriptlettextattributes.md)|Retourne les attributs du texte d'un scriptlet.|  
|[IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)|Retourne les attributs du texte d'un bloc de script.|  
|[IActiveScriptAuthor::IsCommitChar](../../winscript/reference/iactivescriptauthor-iscommitchar.md)|Retourne une valeur qui indique si un caractère spécifié doit valider une saisie semi\-automatique des instructions par l'application.|  
|[IActiveScriptAuthor::ParseScriptText](../../winscript/reference/iactivescriptauthor-parsescripttext.md)|Analyse le texte de script, ajoute du texte au moteur de création de script de création, et crée un objet d' `IScriptEntry` qui correspond au bloc de script.|  
|[IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)|Supprime un objet d' `NamedItem` de l'espace de noms du moteur de création de script.|  
|[IActiveScriptAuthor::RemoveTypeLib](../../winscript/reference/iactivescriptauthor-removetypelib.md)|Supprime une bibliothèque de types de l'espace de noms du moteur de création de script.|  
  
## Voir aussi  
 [Création de script actif, interfaces](../../winscript/reference/active-script-authoring-interfaces.md)