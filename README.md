#DNN=VRG
####Про вариационную рг
В статфизике мы часто рассматриваем ансамбль N спинов $v_i$ которые принимают значения $\pm1$, где под индексом  $i$ понимаем положение спина $v_i$ в некой решетке. В тд пределе, вероятность спина определяется распределением Больцмана
$$P(\{v_i\}) = \frac{e^{-H(\{v_i\})}}{\mathcal Z}$$
где мы определили Гамильтониан $\mathbf H(\{v_i\})$ и стат сумму
$$Z = Tr_{v_i}e^{-H(\{v_i\})} \equiv \sum_{v_i,...v_N = \pm 1}e^{-\mathbf H(\{v_i\})}  $$ 
температура =1. Как правило, гамильтониан зависит от набора связей или параметров $\mathbf K=\{K_s\}$. Например, для бинарного спина, $\mathbf K$: 
$$\mathbf H[\{v_i\}] = -\sum_i K_i v_i - \sum_{ij}K_{ij}v_iv_j - \sum_{ijk}K_{ijk}v_iv_jv_k + .... $$
и можем задать энергию системы спинов как обычно:
$$F^v = -\log Z = -\log({Tr_{v_i} e^{-\mathbf H(\{v_i\})} }) $$
Идея РГ состоит в нахождении нового грубого описания системы спинов в котором "проинтегрированы" колебания малых расстояний. С этой целью введем $M < N$ новых бинарных спинов $\{h_j\}$. Каждый из этих спинов $h_j$ будет хранить грубую степень свободы где флуктуации на малых масштабах усреднены. Как правило подобные огрубляющие методы увеличивают некую характерную величину масштаба описываемой системы, в данном случае размера между узлами решетки. Например, в блок спин ренормализационной картине, введенной Кадановым, каждый $h_j$ показывающий состояние определнного локального блока физических спинов, $v_i$.
На рисунке 1 видна процедура блок-спина двумерной системы спинов на квадратоной решетке, где каждый $ h_j $ представляет $2 \times 2$ блок видимых спинов. Как результат этой огрубляющей процедуры в том, что расстояние между узлами решетки удваивается на каждом таком шаге. 
В общем случае, взаимодействия (статические корелляции) между ${v_i}$ побуждают взаимодействия крупнозернистых спинов ${h_j}$. В частности, крупнозернистые системы могут быть описаны новым крупнозернистым Гамильтонианом вида
$$\mathbf H^{RG} [\{h_j\}] = -\sum_i \tilde K_i h_i - \sum_{ij}\tilde K_{ij}h_ih_j - \sum_{ijk}\tilde K_{ijk}h_ih_jh_k + ..., $$
где $\{\tilde K \}$ описывает взаимодействия между скрытыми спинами, $\{h_j\}$. В физической литературе такое ренормализационное преобразование часто обозначается как отображение между связями, $\{ K \} \to  \{\tilde K\}$. Конечно, точное отображение зависит от особенностей используемой РГ схемы.
В предложенной Кадановым РГ схеме, процедура огрубления реализована строительной функцией(constructing) $\mathbf T_\lambda (\{v_i\},\{h_j\}) $, которая зависит от набора вариационных параметров $\{\lambda \}$ и кодирует (обычно попарно) взаимодействия между физическими и крупнозернистыми степенями свободы. После связи вспомогательных спинов $\{h_j\}$ к физическим спинам $\{v_i\}$, можно проинтегрировать видимые спины для перехода к грубому описанию физической системы в терминах $\{h_j\}$. Тогда функция $\mathbf T_\lambda (\{v_i\},\{h_j\}) $ определяет гамильтониан для $\{h_j\}$ через выражение
$$ e^{\mathbf H^{RG} [\{h_j\}]} \equiv Tr_{v_i}e^{\mathbf T_\lambda (\{v_i\},\{h_j\}) - \mathbf H[\{v_i\}]}$$ 
Также мы можем определить свободную энергию для преобразованной системы обычным образом:
$$F^h_\lambda = -\log({Tr_{h_i} e^{-\mathbf H^{RG}_\lambda(\{h_j\})} }) $$
До сих пор мы игнорировали проблему выбора вариационных параметров $\lambda$, которые определяют нашу РГ трансформацию  $\mathbf T_\lambda (\{v_i\},\{h_j\}) $ Интуитивно ясно, что мы должны выбрать $\lambda$ таким образом, чтобы обеспечить крупномасштабные наблюдения системы инвариантностью относительно такого преобразования. Это делается путем выбора параметров $\lambda$ так, чтобы минимизировать разницу свободных энергий: $\Delta F = F^h_\lambda - F^v$.
$$ \Delta F = 0 \Leftrightarrow Tr_{h_j}e^{\mathbf T_\lambda (\{v_i\},\{h_j\}) }  = 1$$ 
Таким образом, для любомго *точного* РГ преобразования, должно выполняться
$$Tr_{h_j}e^{\mathbf T_\lambda (\{v_i\},\{h_j\}) }  = 1$$
В общем случае, невозможно выбрать параметры $\lambda$ для удовлетворения условия выше и существует множество схем для выбора $\lambda$ минимизирующих этот $\Delta F $ 
#### Ограниченная машина больцмана глубокие нейронные сети
Покажем, что вариационный метод РГ естественным образом интерпретируется как схема глубокого обучения, основанной на мощном классе моделей, основанных на энергии - ограниченных машин больцмана [[1]](#references) мы ограничимся бинарными данными, полученным из некого вероятностного распределения $P(\{v_i\})$, с бинарными спинами $\{v_i\}$, обозначенными индексами $i = 1...N$. Например, для чернобелого изображения каждый спин $\{v_i\}$ определет, является ли данный пиксель включенными или выключенным, а распределение $P(\{v_i\})$  определяет статистические свойства ансамбля картинок.  (Например, набор картинок рукописных цифр из данных MNIST)
<img src="http://corochann.com/wp-content/uploads/2017/02/mnist_plot.png" width="400px"/>
Для моделирования распределения данных, РБМ вводят новые скрытые спиновые переменные  $\{h_j\} (j = 1...M)$ которые соединены с видимыми. Взаимодействия между видимыми и скрытыми узлами моделируется с помощью функции энергии вида
$$\mathbf E(\{v_i\}, \{h_i\}) = \sum_ib_jh_j + \sum_{ij}v_iw_{ij}h_j + \sum_ic_iv_i$$,
где $\lambda = \{b_j,w_{ij},c_i\} $ является вариационным параметром модели. В терминах этой функции энергии, общая вероятность наблюдения конфигурации скрытых и видимых спинов может быть записана как
$$p_\lambda(\{v_i\}, \{h_j\}) = \frac{e^{-\mathbf E(\{v_i\},\{h_j\})}}{\mathcal Z}$$
Такое распределение также определяет вариационное распределение для видимых спинов
$$p_\lambda(\{v_i\}) = \sum_{\{h_j\}}p_\lambda(\{v_i\}, \{h_j\}) = Tr_{h_j}p_\lambda(\{v_i\}, \{h_j\}) $$
как и для распределения скрытых:
$$p_\lambda(\{h_j\}) = \sum_{\{v_i\}}p_\lambda(\{v_i\}, \{h_j\}) = Tr_{v_i}p_\lambda(\{v_i\}, \{h_j\}) $$
В итоге получаем выражение для "вариационного" РБМ гамильтониана для видимых узлов:
$$p(\{v_i\}) \equiv \frac{e^{-\mathbf H^{RBM}_\lambda[\{v_i\}]}}{\mathcal Z}$$
и для скрытых:
$$p(\{h_j\}) \equiv \frac{e^{-\mathbf H^{RBM}_\lambda[\{h_j\}]}}{\mathcal Z}$$
Поскольку цель нашей РБМ в бесконтрольном обучении, параметры выбираются минимизированием расстояния [Кульбака-Лейблера](https://ru.wikipedia.org/wiki/Расстояние_Кульбака_—_Лейблера) между действительным распределением данных $P(\{v_i\})$ и вариационным распределением $p_\lambda(\{v_i\})$:
$$D_{KL}((P(\{v_i\})||p_\lambda(\{v_i\})) = \sum_{\{v_i\}} P(\{v_i\}) \log \frac {P(\{v_i\})}{p_\lambda(\{v_i\})}. $$
Отметим, что когда наша РБМ в точности воспроизводит распределение видимых данных,
$$D_{KL}((P(\{v_i\})||p_\lambda(\{v_i\}))=0$$
В общем случае невозможно однозначно минимизировать $D_{KL}((P(\{v_i\})||p_\lambda(\{v_i\})) $ и приходится использовать различные приближенные численные методы (например, contrastive divergence [[24]](#ref)). Отметим также, что что число скрытых узлов ограничено (меньше чем $2^N$) сделовательно не получится создать точное произвольное распределение.
В глубоких нейронных сетях, рбм сложены друг на друга, когда-то обученные скрытые слои одной РБМ выступают видимыми слоями для следующей РБМ. В частности можно отобразить конфигурацию видимых узлов к конфигурации скрытого слоя через условное вероятностное распределение $p_\lambda(\{v_i\}|\{h_j\})$. Таким образом, после тренировки РБМ мы можем рассмотреть действия скрытого слоя в ответ на каждый видимый пример как данные для обучения второго слоя скрытых спинов и так далее.
#### Отображение ВРГ на  ДНН
В вариационной рг связи между скрытыми и видимыми узлами определяются оператором $\mathbf T_\lambda (\{v_i\},\{h_j\})$ . В РБМ аналогичную роль играет функция общей энергии $\mathbf E (\{v_i\},\{h_j\})$. Фактически, как мы покажем ниже, они связаны выражением,
$$\mathbf T_\lambda (\{v_i\},\{h_j\}) = - \mathbf E (\{v_i\},\{h_j\}) + \mathbf H[\{v_i\}],$$
где $\mathbf H[\{v_i\}]$ - Гамильтониан, определеный в [Уравнении 3](#refeq.3) который определяет вероятность распределения данных $P(\{v_i\}).$
Пользуясь этим определением, просто показать, что гамильтониан $\mathbf H^{RG}_\lambda[\{v_i\}]$ изначально определенный в [Уравнении 6](#refeq.6) как Гамильтониан грубых степеней свободы после рг-преобразования, также описывает скрытые спины РБМ. Это эквивалентно удтверждению, что предельное распределение $p_\lambda(\{h_j\})$ описывающее скрытые спины рбм это больцмановская форма с гамильтонианом $\mathbf H^{RG}_\lambda[\{v_i\}]$. Для доказательства этого разделим обе части [Уравнения 6](#refeq.6) на $\mathcal Z$

$$ \frac {e^{\mathbf H^{RG} [\{h_j\}]}}{\mathcal Z} = \frac {Tr_{v_i}e^{\mathbf T_\lambda (\{v_i\},\{h_j\}) - \mathbf H[\{v_i\}]}}{\mathcal Z}$$ 
Подставив сюда [Уравнение 18](#refeq.18), получим
$$ \frac {e^{\mathbf H^{RG} [\{h_j\}]}}{\mathcal Z} =Tr_{v_i} \frac {e^{\mathbf E (\{v_i\},\{h_j\})}}{\mathcal Z} = p_\lambda(\{h_j\})$$ 
Согласно [Уравнению 15](#refeq.15) 
$$\mathbf H^{RG}_\lambda[\{h_j\}] = \mathbf H^{RBM}_\lambda[\{h_j\}]$$
Такой результат естественным образом полностью интерпретирует вариационную РГ прямиком в язык вероятностей. Оператор $\mathbf T_\lambda (\{v_i\},\{h_j\})$ можно рассматривать как вариационную аппроксимацию условной вероятности скрытых спинов для заданных видимых. 
$$
e^{\mathbf T_\lambda (\{v_i\},\{h_j\})} = e^{\mathbf E (\{v_i\},\{h_j\}) + \mathbf H [\{v_i\}]} \\
= \frac{p_\lambda(\{v_i\}, \{h_j\})}{p_\lambda(\{v_i\})}e^{\mathbf H [\{v_i\}] - \mathbf H^{RBM}_\lambda [\{v_i\}]} \\
= p_\lambda(\{v_i\}| \{h_j\})e^{\mathbf H [\{v_i\}] - \mathbf H^{RBM}_\lambda [\{v_i\}]}
 $$
 Где первый переход с помощью уравнений [11](#refeq11) и [14](#refeq14). Из этого следует что когда РГ выполняется точно (т.е. РГ преобразование удовлетворяет выражению $Tr_{h_j}e^{\mathbf T_\lambda (\{v_i\},\{h_j\}) }  = 1$ ), вариационный Гамильтониан идентичен действительному гамильтониану, описывающему данные, $\mathbf H[\{v_i\}] = \mathbf H^{RBM}_\lambda[\{v_i\}]$ а $\mathbf T[\{v_i\},\{h_j\}]$ условной вероятности. На языке теории вероятностей, это означает, что вариационное распределение $p_\lambda( \{v_i\})$ точно отражает действительное распределение данных $P(\{v_i\})$, и $D_{KL}((P(\{v_i\})||p_\lambda(\{v_i\}))=0$
 В общем случае невозможно точно выполнить РГ преобразование. Вместо этого можно создать семейство вариационных аппроксимаций точного РГ преобразования. Обсуждения выше делают понятным то, что эти вариационные распределения арботают  на уровне Гамильтонианов и Свободных Энергий. С другой стороны, в источниках по машинному обучению эти вариационные аппроксимации обычно получаются путем минимизации расстояния Кульбака-Лейблера $D_{KL}((P(\{v_i\})||p_\lambda(\{v_i\}))=0$. Таким образом оба подхода используют вариационные аппроксимационные схемы для грубого масштаба. Заметим, наконец, что это соответствие не зависит от явного вида энергии $\mathbf E (\{v_i\},\{h_j\})$, следовательно применимо для любой машины Больцмана.



> Written with [StackEdit](https://stackedit.io/).

#### Использованная литература

[1] G.E. Hinton ... Signal Processing Magazine 2012
[24] G.E. Hinton 2002 Neural computation
