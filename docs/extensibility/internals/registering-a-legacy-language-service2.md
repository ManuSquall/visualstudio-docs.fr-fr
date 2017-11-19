---
title: "L’inscription d’un Service2 de langage hérité | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, language services
- language services, registry information
- registry, language services
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f64b02521fcea9abef9d7196a27e4a209100a892
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="registering-a-legacy-language-service"></a>L’inscription d’un Service de langage hérité
Les sections suivantes fournissent des listes d’entrées de Registre pour la langue différentes options de service disponibles dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Dans la liste suivante d’entrées de Registre, *VS Reg racine* est égal à HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*X.Y*, où *X.Y* est le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] numéro de version.  
  
## <a name="registry-entries-for-language-service-options"></a>Entrées de Registre pour les Options de Service de langage  
 Le *VS Reg racine*\Languages\Language Services\\*nom de la langue* clé peut contenir les valeurs suivantes.  
  
|Nom|Type|Range|Description|  
|----------|----------|-----------|-----------------|  
|(Default)|REG_SZ|*\<GUID >*|GUID du service de langage.|  
|LangResID|REG_DWORD|0 x 0-0xffff|Identificateur de ressource (ResID) pour le nom localisé de la langue de la chaîne.|  
|Package|REG_SZ|*\<GUID >*|GUID du VSPackage.|  
|ShowCompletion|REG_DWORD|0-1|Spécifie si le **saisie semi-automatique des instructions** options dans le **Options** boîte de dialogue sont activés.|  
|ShowSmartIndent|REG_DWORD|0-1|Spécifie si l’option pour sélectionner **Smart** mise en retrait dans les **Options** boîte de dialogue est activée.|  
|RequestStockColors|REG_DWORD|0-1|Spécifie si personnalisés ou les couleurs par défaut sont utilisées pour la couleur des mots clés.|  
|ShowHotURLs|REG_DWORD|0-1|Spécifie si l’utilisateur peut cliquer sur des URL.|  
|Par défaut aux URL Non réactif|REG_DWORD|0-1|Spécifie le paramètre initial pour le **activer la navigation dans les URL par simple clic** option dans le **Options** boîte de dialogue.|  
|DefaultToInsertSpaces|REG_DWORD|0-1|Spécifie si le service de langage a « Insérer des espaces » en tant que son option de l’onglet par défaut.|  
|ShowDropdownBarOption|REG_DWORD|0-1|Active ou désactive le **barre de Navigation** option dans le **Options** boîte de dialogue qui affiche ou masque le **barre de Navigation**.|  
|Que la fenêtre de Code unique|REG_DWORD|0-1|Active ou désactive le **nouvelle fenêtre** choix dans le **fenêtre** menu pour un service de langage.|  
|EnableAdvancedMembersOption|REG_DWORD|0-1|Active ou désactive un **Options** paramètre de la boîte de dialogue zone **masquer les membres avancés**.|  
|Prise en charge CF_HTML|REG_DWORD|0-1|Spécifie si l’éditeur permet de copier et coller des données HTML.|  
|EnableLineNumbersOption|REG_DWORD|0-1|Spécifie si le **numéros de ligne** options dans le **Options** boîte de dialogue est activée pour un service de langage.|  
|HideAdvancedMembersByDefault|REG_DWORD|0-1|Spécifie si les membres avancés tels que des champs privés sont masquées dans les listes de saisie semi-automatique.|  
|ShowBraceCompletion|REG_DWORD|0-1|Spécifie si le **accolade de fin** option dans le **Options** boîte de dialogue est activée.|  
  
### <a name="example"></a>Exemple  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      C/C++\  
        (Default)             = reg_sz:{B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}  
        LangResID             = reg_dword:0x00000000  
        Package               = reg_sz:{8C2EA640-ABC1-11D0-9D62-00C04FD9DFD9}  
        ShowCompletion        = reg_dword:0x00000001  
        ShowSmartIndent       = reg_dword:0x00000001  
        ShowDropdownBarOption = reg_dword:0x00000001  
```  
  
## <a name="registry-entries-for-debugger-languages-options"></a>Entrées de Registre pour les Options du débogueur de langages  
 Le *VS Reg racine*\Languages\Language Services\\*nom de la langue*\Debugger langues\\*GUID*\ clé peut inclure les éléments suivants valeurs.  
  
|Nom|Type|Range|Description|  
|----------|----------|-----------|-----------------|  
|(Default)|REG_SZ|ASCII|La valeur par défaut peut être utilisée pour le nom de la langue du document. Le nom de cette clé est un GUID de l’évaluateur d’expression qui a une entrée correspondante dans  *\<VS Reg racine >*\AD7Metrics\Expression évaluateur.|  
  
### <a name="example"></a>Exemple  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      C/C++\  
        Debugger Languages\  
          {3A12D0B7-C26C-11D0-B442-00A0244A1DD2}\  
            (Default) = reg_sz:C++  
```  
  
## <a name="registry-entries-for-editor-tools-options"></a>Entrées de Registre pour les Options des outils de l’éditeur  
 Vous pouvez ajouter des clés de Registre sous la clé EditorToolsOptions pour les pages de propriétés et les nœuds de la propriété. Ces clés et leurs valeurs identifient les pages de propriétés de la **Options** boîte de dialogue (sur le **outils** menu) qui sont utilisés pour configurer le service de langage. Dans l’exemple suivant, *nom de la Page* est le nom d’une page de propriétés, et *nom de nœud* est le nom d’un nœud dans l’arborescence sur la **Options** boîte de dialogue. L’entrée de la page et l’entrée de nœud doivent être spécifiées séparément.  
  
|Nom|Type|Range|Description|  
|----------|----------|-----------|-----------------|  
|(Default)|REG_SZ|ResID|Le nom complet localisé de cette page d’options. Le nom peut être texte littéral ou #`nnn`, où `nnn` est un ID de ressource de chaîne dans la DLL du VSPackage spécifié satellite.|  
|Package|REG_SZ|*GUID*|Le GUID du VSPackage qui implémente cette page d’options.|  
|Page|REG_SZ|*GUID*|Le GUID de la page de propriétés pour demander au VSPackage en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> (méthode). Si cette entrée de Registre n’est pas présente, la clé de Registre décrit un nœud, et non pas une page.|  
  
### <a name="example"></a>Exemple  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      CSharp\  
        EditorToolsOptions\  
          Formatting\  
            (Default) = reg_sz:#242  
            Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
            General\  
              (Default) = reg_sz:#255  
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
              Page      = reg_sz:{3EB2CC0B-033E-4D75-B26A-B2362C25227E}  
            Indentation\  
              (Default) = reg_sz:#250  
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
              Page      = reg_sz:{5E21D017-6D2A-4114-A1F1-C923F001CBBB}  
            Newlines\  
              (Default) = reg_sz:#253  
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
              Page      = reg_sz:{607D8062-68D1-41E4-9A35-B5E7F14D0481}  
```  
  
## <a name="registry-entries-for-file-name-extension-options"></a>Entrées de Registre pour les Options d’Extension de nom de fichier  
 L’entrée pour l’extension de fichier doit inclure le point, par exemple « .myext ».  
  
|Nom|Type|Range|Description|  
|----------|----------|-----------|-----------------|  
|(Default)|REG_SZ|*GUID*|GUID du service pour le service de langage par défaut pour ce type d’extension de nom du fichier.|  
  
### <a name="example"></a>Exemple  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    File Extensions\  
      .cpp\  
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}  
```  
  
## <a name="registry-entries-for-editor-options"></a>Entrées de Registre pour les Options de l’éditeur  
 Le *VS Reg racine*\Editors clé peut contenir les valeurs suivantes :  
  
|Nom|Type|Range|Description|  
|----------|----------|-----------|-----------------|  
|(Default)|REG_SZ|""|N’est pas utilisé ; Vous pouvez placer votre nom ici pour obtenir la documentation.|  
|DefaultToolboxTab|REG_SZ|""|Nom de l’onglet Boîte à outils à utiliser par défaut lors de l’éditeur est actif.|  
|DisplayName|REG_SZ|ResID|Nom à afficher dans le **ouvrir avec** boîte de dialogue. Le nom est l’ID de ressource de chaîne ou un nom de format standard.|  
|ExcludeDefTextEditor|REG_DWORD|0-1|Utilisé pour le **ouvrir avec** commande de menu. Si vous ne souhaitez pas que l’éditeur de texte par défaut dans la liste des éditeurs disponibles pour un type de fichier de liste, définissez cette valeur sur 1.|  
|LinkedEditorGUID|REG_SZ|*\<GUID >*|Utilisé pour n’importe quel service de langage que vous pouvez ouvrir un fichier avec prise en charge de la page de codes. Par exemple, lorsque vous ouvrez un fichier .txt à l’aide de la **ouvrir avec** commande, les options sont fournies pour l’utilisation de l’éditeur de code source avec et sans encodage.<br /><br /> Le GUID spécifié dans le nom de la sous-clé est pour la fabrique d’éditeur de page de codes ; le GUID lié spécifié dans cette entrée de Registre spécifique est pour la fabrique d’éditeur standard. L’objectif de cette entrée est que si l’IDE n’ouvre pas un fichier à l’aide de l’éditeur par défaut, l’IDE essaient d’utiliser l’éditeur suivant dans la liste. Cet éditeur suivant ne doit pas être la fabrique d’éditeur de page de codes, car cette fabrique d’éditeur est essentiellement le même que la fabrique d’éditeur qui a échoué.|  
|Package|REG_SZ|*\<GUID >*|VSPackage GUID pour ResID du nom affichage.|  
  
### <a name="example"></a>Exemple  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  \Editors\  
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\  
      (Default)            = reg_sz:Html Editor with Encoding  
      DefaultToolboxTab    = reg_sz:HTML  
      DisplayName          = reg_sz:#20101  
      LinkedEditorGUID     = reg_sz:{C76D83F8-A489-11D0-8195-00A0C91BBEE3}  
      Package              = reg_sz:{1B437D20-F8FE-11D2-A6AE-00104BCC7269}  
```  
  
## <a name="registry-entries-for-logical-view-options"></a>Entrées de Registre pour les Options de vue logique  
 Le *VS Reg racine*\Editors\\*éditeur de l’interface graphique utilisateur >*\LogicalViews clé peut contenir les valeurs suivantes.  
  
|Nom|Type|Range|Description|  
|----------|----------|-----------|-----------------|  
|(Default)|REG_SZ||Non utilisé.|  
|*\<GUID >*|REG_SZ|""|Clé aux logiques vues prises en charge. Vous pouvez avoir autant que nécessaire. Le nom de l’entrée de Registre est ce qui est important, pas la valeur, qui est toujours une chaîne vide.|  
  
### <a name="example"></a>Exemple  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  \Editors\  
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\  
      LogicalViews\  
       (Default) = reg_sz:  
       {7651a700-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
       {7651a701-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
       {7651a702-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
       {7651a703-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
```  
  
## <a name="registry-entries-for-editor-extension-options"></a>Entrées de Registre pour les Options d’Extension de l’éditeur  
 Le *VS Reg racine*\Editors\\*éditeur GUID*\Extensions clé peut contenir les valeurs suivantes. L’extension de nom de fichier n’inclut pas le point de début.  
  
|Nom|Type|Range|Description|  
|----------|----------|-----------|-----------------|  
|(Default)|REG_SZ||Non utilisé.|  
|*\<ext >*|REG_DWORD|0-0xffffffff.|Priorité relative des extensions. Si deux ou plusieurs langues partagent la même extension, la langue de priorité plus élevée est choisie.|  
  
 En outre, la sélection par défaut de l’utilisateur actuel pour un éditeur est stockée dans HKEY_Current_User\Software\Microsoft\VisualStudio\\*X.Y*\Default éditeurs\\*ext*. Le GUID du service de langage sélectionné est dans l’entrée personnalisée. Cet événement est prioritaire pour l’utilisateur actuel.  
  
### <a name="example"></a>Exemple  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\  
  \Editors\  
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\  
      Extensions\  
       (Default) = reg_sz:  
       *         = reg_dword:0x00000018  
       html      = reg_dword:0x00000027  
       shtm      = reg_dword:0x00000027  
       shtml     = reg_dword:0x00000027  
```  
  
## <a name="registry-entries-for-managed-package-framework-language-service-options"></a>Entrées de Registre pour les Options de Service de langage Managed Package Framework  
 Les entrées de Registre suivantes concernent les classes de service de langage managé package framework (MPF). Ces entrées de Registre indiquent la prise en charge dans le service de langage pour les diverses fonctionnalités d’IntelliSense et d’autres fonctionnalités d’éditions avancées.  
  
 Ces entrées de Registre sont accessibles via la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe.  
  
|Nom|Type|Range|Description|  
|----------|----------|-----------|-----------------|  
|CodeSense|REG_DWORD|0-1|Prise en charge pour les opérations d’IntelliSense.|  
|MatchBraces|REG_DWORD|0-1|Prise en charge pour la correspondance des paires de langage telles que des accolades, parenthèses et crochets.|  
|Info express|REG_DWORD|0-1|Prise en charge pour l’opération Info express IntelliSense.|  
|ShowMatchingBrace|REG_DWORD|0-1|Prise en charge pour l’affichage de la paire de langue correspondante dans la barre d’état.|  
|MatchBracesAtCaret|REG_DWORD|0-1|Prise en charge pour l’affichage des paires correspondantes de langage, généralement par le biais de la mise en surbrillance les deux éléments.|  
|MaxErrorMessages|REG_DWORD|0-n|Le nombre maximal d’erreurs qui peuvent être affichés dans le **liste d’erreurs** fenêtre.|  
|CodeSenseDelay|REG_DWORD|0-n|Le nombre de millisecondes à attendre avant le lancement de n’importe quel arrière-plan l’analyse pour une opération IntelliSense.|  
|EnableAsyncCompletion|REG_DWORD|0-1|Prise en charge pour l’analyse en arrière-plan.|  
|EnableCommenting|REG_DWORD|0-1|Prise en charge pour commenter des blocs de texte sélectionnés et implique également la prise en charge pour le texte sélectionné de supprimer le commentaire.|  
|EnableFormatSelection|REG_DWORD|0-1|Prise en charge pour la mise en forme de texte tel qu’auto-mise en retrait ou d’ajustement de la position des accolades.|  
|AutoOutlining|REG_DWORD|0-1|Prise en charge (régions qui peuvent être réduites) en mode plan.|  
|MaxRegions|REG_DWORD|0-n|Le nombre maximal de zones masquées par fichier.|  
  
```  
ExampleHKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      XML\  
        (Default)             = reg_sz:{f6819a78-a205-47b5-be1c-675b3c7f0b8e}  
        MatchBraces           = reg_dword:0x00000001  
        QuickInfo             = reg_dword:0x00000001  
        ShowMatchingBrace     = reg_dword:0x00000001  
        MatchBracesAtCaret    = reg_dword:0x00000000  
        MaxErrorMessages      = reg_dword:0x00000064  
        CodeSenseDelay        = reg_dword:0x000001f4  
        MaxRegions            = reg_dword:0x0000000a  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’un service de langage hérité](../../extensibility/internals/developing-a-legacy-language-service.md)