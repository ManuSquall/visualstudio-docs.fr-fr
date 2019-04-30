---
title: Analyser l’utilisation du processeur dans une application universelle Windows | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c122b08e-e3bf-43e6-bd6c-e776e178fd9a
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: 646bba541e18fd372bd5236f7ebb6b91d1472d55
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435085"
---
# <a name="analyze-cpu-usage-in-a-windows-universal-app"></a>Analyser l’utilisation du processeur dans une application universelle Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

S’applique à Windows et Windows Phone] (.. /Image/windows_and_phone_content.png « windows_and_phone_content »)  
  
 Lorsque vous devez étudier les problèmes de performances de votre application, un bon point de départ consiste à comprendre son utilisation du processeur. L’outil **Utilisation de l’UC** vous montre à quels endroits le processeur est utilisé pour l’exécution de code. Pour se concentrer sur des scénarios spécifiques, l’outil Utilisation de l’UC peut être exécuté avec l’outil [Réactivité de l'interface utilisateur XAML](http://msdn.microsoft.com/library/4ff84cd1-4e63-4fda-b34f-3ef862a6e480), avec l’outil [Consommation d’énergie](../profiling/analyze-energy-use-in-store-apps.md) ou avec ces deux outils dans une même session de diagnostic.  
  
> [!NOTE]
> L’outil **Utilisation de l’UC** ne peut pas être utilisé avec les applications Silverlight Windows Phone 8.1.  
  
 Cette procédure pas à pas vous guide tout au long de la collecte et de l’analyse des données liées à l’utilisation du processeur pour une application XAML universelle Windows simple.  
  
## <a name="BKMK_Create_the_CpuUseDemo_project"></a> Créer le projet CpuUseDemo  
 L’application **CpuUseDemo** a été créée pour expliquer comment collecter et analyser les données d’utilisation de l’UC. Les boutons génèrent un nombre en appelant une méthode qui sélectionne la valeur maximale de plusieurs appels à une fonction. La fonction appelée crée un très grand nombre de valeurs aléatoires, puis retourne la dernière. Les données sont affichées dans une zone de texte.  
  
1. Créez un projet d’application universelle Windows en C# nommé **CpuUseDemo**, à l’aide du modèle **BlankApp**.  
  
     ![Créer le projet CpuUseDemo](../profiling/media/cpu-use-newproject.png "CPU_USE_NewProject")  
  
2. Remplacez MainPage.xaml par [ce code](#BKMK_MainPage_xaml).  
  
3. Remplacez MainPage.xaml.cs par [ce code](#BKMK_MainPage_xaml_cs).  
  
4. Générez l'application et essayez-la. L’application est simple et vous montre certains cas courants d’analyse des données liées à l’utilisation du processeur.  
  
## <a name="BKMK_Collect_CPU_usage_data"></a> Collecter les données d'utilisation de l'UC  
 ![Exécuter une version Release de l’application dans le simulateur](../profiling/media/cpu-use-wt-setsimulatorandretail.png "CPU_USE_WT_SetSimulatorAndRetail")  
  
1. Dans Visual Studio, définissez la cible de déploiement sur **Simulateur**, et la configuration de la solution sur **Mise en production**.  
  
   - L’exécution de l’application dans le simulateur vous permet de passer facilement de l’application à l’interface IDE de Visual Studio.  
  
   - L’exécution de cette application en mode **Mise en production** vous donne un meilleur aperçu des performances réelles de votre application.  
  
2. Dans le menu **Déboguer** , choisissez **Profileur de performances**.  
  
3. Dans le hub Performances et diagnostics, choisissez **Utilisation de l’UC**, puis **Démarrer**.  
  
    ![Démarrer la session de diagnostic CpuUsage](../profiling/media/cpu-use-wt-perfdiaghub.png "CPU_USE_WT_PerfDiagHub")  
  
4. Lorsque l'application démarre, cliquez sur **Obtenir le nombre maximal**. Attendez environ une seconde après que la sortie s'est affichée, puis choisissez **Obtenir le nombre maximal asynchrone**. L'attente entre les clics de bouton permet plus facilement d'isoler les routines de clic de bouton dans le rapport de diagnostic.  
  
5. Quand apparaît la deuxième ligne de sortie, choisissez **Arrêter la collecte** dans le hub Performances et diagnostics.  
  
   ![Arrêter la collecte des données CpuUsage](../profiling/media/cpu-use-wt-stopcollection.png "CPU_USE_WT_StopCollection")  
  
   L'outil Utilisation de l'UC analyse les données et affiche le rapport.  
  
   ![Rapport CpuUsage](../profiling/media/cpu-use-wt-report.png "CPU_USE_WT_Report")  
  
## <a name="BKMK_Analyze_the_CPU_Usage_report"></a> Analyser le rapport d’utilisation de l’UC  
  
### <a name="BKMK_CPU_utilization_timeline_graph"></a> Graphique chronologique d’utilisation de l’UC  
 ![Graphique chronologique CpuUtilization &#40;%&#41;](../profiling/media/cpu-use-wt-timelinegraph.png "CPU_USE_WT_TimelineGraph")  
  
 Le graphique d'utilisation de l'UC indique l'activité processeur de l'application sous forme de pourcentage du temps processeur total de tous les processeurs de l'appareil. Les données de ce rapport ont été collectées sur une machine double cœur. Les deux grandes pointes représentent l'activité processeur de deux clics de bouton. `GetMaxNumberButton_Click` s'effectue de manière synchrone sur un seul cœur, il est donc normal que la hauteur du graphique de la méthode ne dépasse jamais 50 %. `GetMaxNumberAsycButton_Click` s'exécute de manière asynchrone sur les deux cœurs, il est donc également normal que sa pointe soit presqu'aussi élevée qu'en cas d'utilisation de toutes les ressources processeur sur les deux cœurs.  
  
#### <a name="BKMK_Select_timeline_segments_to_view_details"></a> Sélectionner des segments chronologiques pour afficher les détails  
 Utilisez les barres de sélection de la chronologie de la **Session de diagnostic** pour vous concentrer sur les données de GetMaxNumberButton_Click :  
  
 ![GetMaxNumberButton&#95;Click sélectionné](../profiling/media/cpu-use-wt-getmaxnumberreport.png "CPU_USE_WT_GetMaxNumberReport")  
  
 La chronologie de la **Session de diagnostic** affiche désormais la durée d’utilisation pour le segment sélectionné (un peu plus de 2 secondes dans ce rapport) et filtre l’arborescence des appels sur les méthodes exécutées dans la sélection.  
  
 Sélectionnez maintenant le segment `GetMaxNumberAsyncButton_Click`.  
  
 ![Sélection du rapport GetMaxNumberAsyncButton&#95;Click](../profiling/media/cpu-use-wt-getmaxnumberasync-selected.png "CPU_USE_WT_GetMaxNumberAsync_Selected")  
  
 Cette méthode se termine environ une seconde plus rapidement que `GetMaxNumberButton_Click`, mais la signification des entrées de l'arborescence des appels est moins évidente.  
  
### <a name="BKMK_The_CPU_Usage_call_tree"></a> Arborescence des appels - Utilisation du processeur  
 Pour commencer la présentation des informations sur l'arborescence des appels, sélectionnez de nouveau le segment `GetMaxNumberButton_Click` et consultez les détails d'arborescence des appels.  
  
#### <a name="BKMK_Call_tree_structure"></a> Structure de l’arborescence des appels  
 ![Arborescence des appels GetMaxNumberButton&#95;Click](../profiling/media/cpu-use-wt-getmaxnumbercalltree-annotated.png "CPU_USE_WT_GetMaxNumberCallTree_annotated")  
  
|||  
|-|-|  
|![Étape 1](../profiling/media/procguid-1.png "ProcGuid_1")|Le nœud de premier niveau des arborescences d'appels de l'outil Utilisation de l'UC est un pseudo-nœud|  
|![Étape 2](../profiling/media/procguid-2.png "ProcGuid_2")|Dans la plupart des applications, quand l'option **Afficher le code externe** est désactivée, le nœud de deuxième niveau est un nœud **[Code externe]** contenant le code système et framework qui démarre et arrête l'application, dessine l'interface utilisateur, contrôle la planification des threads et fournit d'autres services de niveau inférieur à l'application.|  
|![Étape 3](../profiling/media/procguid-3.png "ProcGuid_3")|Les enfants du nœud de deuxième niveau sont les méthodes en code utilisateur et des routines asynchrones appelées ou créées par le code système et framework de deuxième niveau.|  
|![Étape 4](../profiling/media/procguid-4.png "ProcGuid_4")|Les nœuds enfants d'une méthode contiennent des données seulement pour les appels de la méthode parente. Lorsque l'option **Afficher le Code externe** est désactivée, les méthodes d'application peuvent également contenir un nœud **[Code externe]** .|  
  
#### <a name="BKMK_External_Code"></a> Code externe  
 Le code externe est constitué des fonctions des composants système et framework exécutés par le code que vous écrivez. Le code externe comprend des fonctions qui démarrent et arrêtent l’application, dessinent l’interface utilisateur, contrôlent les threads et fournissent d’autres services de bas niveau à l’application. Dans la plupart des cas, vous ne serez pas intéressé par le code externe ; par conséquent, l'arborescence des appels de l'utilisation du processeur regroupe les fonctions externes d'une méthode utilisateur en un seul nœud **[Code externe]** .  
  
 Quand vous voulez afficher les chemins d'appel du code externe, choisissez **Afficher le code externe** dans la liste **Filtrer la vue** , puis **Appliquer**.  
  
 ![Choisir Filtrer l’affichage, puis Afficher le code externe](../profiling/media/cpu-use-wt-filterview.png "CPU_USE_WT_FilterView")  
  
 N'oubliez pas que de nombreuses chaînes d'appel en code externe sont profondément imbriquées, la largeur de la colonne Nom de fonction ne peut pas dépasser la largeur d'affichage de presque tous les moniteurs d'ordinateur, sauf les plus larges. Si tel est le cas, les noms de fonction sont affichés sous forme de **[…]**:  
  
 ![Code externe imbriqué dans l’arborescence des appels](../profiling/media/cpu-use-wt-showexternalcodetoowide.png "CPU_USE_WT_ShowExternalCodeTooWide")  
  
 Utilisez la zone de recherche pour trouver le nœud que vous cherchez, puis utilisez la barre de défilement horizontal pour afficher les données dans la vue :  
  
 ![Rechercher du code externe imbriqué](../profiling/media/cpu-use-wt-showexternalcodetoowide-found.png "CPU_USE_WT_ShowExternalCodeTooWide_Found")  
  
### <a name="BKMK_Call_tree_data_columns"></a> Colonnes des données de l’arborescence des appels  
  
|||  
|-|-|  
|**Processeur total (%)**|![% total, équation de données](../profiling/media/cpu-use-wt-totalpercentequation.png "CPU_USE_WT_TotalPercentEquation")<br /><br /> Pourcentage de l'activité du processeur de l'application dans la plage de temps sélectionnée qui a été utilisé par les appels de la fonction et les fonctions appelées par la fonction. Notez que cette information est différente du graphique chronologique **Utilisation du processeur** qui compare l'activité totale de l'application dans une plage de temps à la capacité totale disponible de l'UC.|  
|**Processeur auto (%)**|![% auto, équation](../profiling/media/cpu-use-wt-selflpercentequation.png "CPU_USE_WT_SelflPercentEquation")<br /><br /> Pourcentage de l'activité du processeur de l'application dans la plage de temps sélectionnée qui a été utilisé par les appels de la fonction, à l'exclusion de l'activité des fonctions appelées par la fonction.|  
|**Total processeur (ms)**|Nombre de millisecondes utilisées par les appels à la fonction dans la plage de temps sélectionnée et les fonctions appelées par la fonction.|  
|**Processeur auto (ms)**|Nombre de millisecondes utilisées par les appels à la fonction dans la plage de temps sélectionnée et les fonctions appelées par la fonction.|  
|**Module**|Nom du module contenant la fonction, ou le nombre de modules contenant les fonctions dans un nœud [Code externe].|  
  
### <a name="BKMK_Asynchronous_functions_in_the_CPU_Usage_call_tree"></a> Fonctions asynchrones de l'arborescence des appels de l'utilisation du processeur  
 Lorsque le compilateur rencontre une méthode asynchrone, il crée une classe masquée pour contrôler l'exécution de la méthode. Conceptuellement, la classe est une machine à états qui inclut la liste des fonctions générées par le compilateur qui appellent les opérations de la méthode d'origine en mode asynchrone, ainsi que les rappels, le planificateur et les itérateurs requis. Quand la méthode d'origine est appelée par une méthode parente, le runtime supprime la méthode du contexte d'exécution du parent et exécute les méthodes de la classe masquée dans le contexte du code système et de l'infrastructure qui contrôle l'exécution de l'application. Les méthodes asynchrones sont souvent, mais pas toujours, exécutées sur un ou plusieurs threads différents. Ce code est affiché dans l'arborescence des appels de l'utilisation du processeur en tant qu'enfants du nœud **[Code externe]** situé immédiatement sous le nœud supérieur de l'arborescence.  
  
 Pour le voir dans notre exemple, resélectionnez le segment `GetMaxNumberAsyncButton_Click` dans la chronologie.  
  
 ![Sélection du rapport GetMaxNumberAsyncButton&#95;Click](../profiling/media/cpu-use-wt-getmaxnumberasync-selected.png "CPU_USE_WT_GetMaxNumberAsync_Selected")  
  
 Les deux premiers nœuds sous **[Code externe]** sont les méthodes générées par le compilateur de la classe de la machine d'état. Le troisième nœud est l'appel de la méthode d'origine. En développant les méthodes générées, vous avez un aperçu de ce qui se passe.  
  
 ![Arborescence des appels GetMaxNumberAsyncButton&#95;Click développée](../profiling/media/cpu-use-wt-getmaxnumberasync-expandedcalltree.png "CPU_USE_WT_GetMaxNumberAsync_ExpandedCallTree")  
  
- `MainPage::GetMaxNumberAsyncButton_Click` se contente de gérer la liste des valeurs de la tâche, de calculer le nombre maximal de résultats et d'affiche la sortie.  
  
- `MainPage+<GetMaxNumberAsyncButton_Click>d__3::MoveNext` affiche l'activité requise pour planifier et lancer les 48 tâches qui encapsulent l'appel à `GetNumberAsync`.  
  
- `MainPage::<GetNumberAsync>b__b` affiche l'activité des tâches qui appellent `GetNumber`.  
  
## <a name="BKMK_Next_steps"></a> Étapes suivantes  
 L'application CpuUseDemo n'est pas la plus sensationnelle des applications, mais vous pouvez étendre son utilité en l'utilisant pour la tester avec le fonctionnement asynchrone et d'autres outils du hub Performances et diagnostics.  
  
- Notez que `MainPage::<GetNumberAsync>b__b` consacre plus de temps au [Code externe] qu'à l'exécution de la méthode GetNumber. Une grande partie de ce temps est consacré au traitement des opérations asynchrones. Essayez d'augmenter le nombre de tâches (défini dans la constante `NUM_TASKS` de MainPage.xaml.cs) et de réduire le nombre d'itérations dans `GetNumber` (modifiez la valeur `MIN_ITERATIONS`). Exécutez le scénario de collecte et comparez l'activité processeur de `MainPage::<GetNumberAsync>b__b` à celle de la session de diagnostic d'Utilisation de l'UC d'origine. Essayez de réduire les tâches et d'augmenter les itérations.  
  
- Souvent, les utilisateurs ne s'intéressent pas aux performances réelles de votre application, mais aux performances perçues et à la réactivité de l'application. L'outil Réactivité de l'interface utilisateur XAML vous montre les détails de l'activité sur le thread d'interface utilisateur qui affecte la perception de la réactivité.  
  
     Créez une session dans le hub Performances et diagnostics et ajoutez les outils Réactivité de l'interface utilisateur XAML et Utilisation de l'UC. Exécutez le scénario de collection. À ce stade, le rapport ne vous dit probablement rien que vous ne sachiez déjà, mais les différences entre les graphiques chronologiques **Utilisation du thread d’interface utilisateur** des deux méthodes sont frappantes. Dans les applications complexes du monde réel, la combinaison des outils peut être très utile.  
  
## <a name="BKMK_MainPage_xaml"></a> MainPage.xaml  
  
```csharp  
<Page  
    x:Class="CpuUseDemo.MainPage"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:local="using:CpuUseDemo"  
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    mc:Ignorable="d">  
  
    <Page.Resources>  
        <Style TargetType="TextBox">  
            <Setter Property="FontFamily"  Value="Lucida Console" />  
        </Style>  
    </Page.Resources>  
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">  
        <Grid.RowDefinitions>  
            <RowDefinition Height="Auto" />  
            <RowDefinition Height="*" />  
        </Grid.RowDefinitions>  
        <StackPanel Grid.Row="0" Orientation="Horizontal"  Margin="0,40,0,0">  
            <Button Name="GetMaxNumberButton" Click="GetMaxNumberButton_Click"  Content="Get Max Number" />  
            <Button Name="GetMaxNumberAsyncButton" Click="GetMaxNumberAsyncButton_Click"  Content="Get Max Number Async" />  
        </StackPanel>  
        <StackPanel Grid.Row="1">  
            <TextBox Name="TextBox1" AcceptsReturn="True" />  
        </StackPanel>  
    </Grid>  
  
</Page>  
  
```  
  
## <a name="BKMK_MainPage_xaml_cs"></a> MainPage.xaml.cs  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.IO;  
using System.Linq;  
using System.Runtime.InteropServices.WindowsRuntime;  
using Windows.Foundation;  
using Windows.Foundation.Collections;  
using Windows.UI.Xaml;  
using Windows.UI.Xaml.Controls;  
using Windows.UI.Xaml.Controls.Primitives;  
using Windows.UI.Xaml.Data;  
using Windows.UI.Xaml.Input;  
using Windows.UI.Xaml.Media;  
using Windows.UI.Xaml.Navigation;  
using Windows.Foundation.Diagnostics;  
using System.Threading;  
using System.Threading.Tasks;  
using System.Collections.Concurrent;  
  
// The Blank Page item template is documented at http://go.microsoft.com/fwlink/?LinkId=234238  
  
namespace CpuUseDemo  
{  
    /// <summary>  
    /// An empty page that can be used on its own or navigated to within a Frame.  
    /// </summary>  
    public sealed partial class MainPage : Page  
    {  
        public MainPage()  
        {  
            this.InitializeComponent();  
        }  
  
        const int NUM_TASKS = 48;  
        const int MIN_ITERATIONS = int.MaxValue / 1000;  
        const int MAX_ITERATIONS = MIN_ITERATIONS + 10000;  
  
        long m_totalIterations = 0;  
        readonly object m_totalItersLock = new object();  
  
        private void GetMaxNumberButton_Click(object sender, RoutedEventArgs e)  
        {  
            GetMaxNumberAsyncButton.IsEnabled = false;  
            lock (m_totalItersLock)  
            {  
                m_totalIterations = 0;  
            }  
            List<int> tasks = new List<int>();  
            for (var i = 0; i < NUM_TASKS; i++)  
            {  
                var result = 0;  
                result = GetNumber();  
                tasks.Add(result);  
            }  
            var max = tasks.Max();  
            var s = GetOutputString("GetMaxNumberButton_Click", NUM_TASKS, max, m_totalIterations);  
            TextBox1.Text += s;  
            GetMaxNumberAsyncButton.IsEnabled = true;  
        }  
  
        private async void GetMaxNumberAsyncButton_Click(object sender, RoutedEventArgs e)  
        {  
            GetMaxNumberButton.IsEnabled = false;  
            GetMaxNumberAsyncButton.IsEnabled = false;  
            lock (m_totalItersLock)  
            {  
                m_totalIterations = 0;  
            }  
            var tasks = new ConcurrentBag<Task<int>>();  
            for (var i = 0; i < NUM_TASKS; i++)  
            {  
                tasks.Add(GetNumberAsync());  
            }  
            await Task.WhenAll(tasks.ToArray());  
            var max = 0;  
            foreach (var task in tasks)  
            {  
                max = Math.Max(max, task.Result);  
            }  
            var func = "GetMaxNumberAsyncButton_Click";  
            var outputText = GetOutputString(func, NUM_TASKS, max, m_totalIterations);  
            TextBox1.Text += outputText;  
            this.GetMaxNumberButton.IsEnabled = true;  
            GetMaxNumberAsyncButton.IsEnabled = true;  
        }  
  
        private int GetNumber()  
        {  
            var rand = new Random();  
            var iters = rand.Next(MIN_ITERATIONS, MAX_ITERATIONS);  
            var result = 0;  
            lock (m_totalItersLock)  
            {  
                m_totalIterations += iters;  
            }  
            // we're just spinning here  
            // and using Random to frustrate compiler optimizations  
            for (var i = 0; i < iters; i++)  
            {  
                result = rand.Next();  
            }  
            return result;  
        }  
  
        private Task<int> GetNumberAsync()  
        {  
            return Task<int>.Run(() =>  
            {  
                return GetNumber();  
            });  
        }  
  
        string GetOutputString(string func, int cycles, int max, long totalIters)  
        {  
            var fmt = "{0,-35}Tasks:{1,3}    Maximum:{2, 12}    Iterations:{3,12}\n";  
            return String.Format(fmt, func, cycles, max, totalIters);  
        }  
  
    }  
}  
  
```
