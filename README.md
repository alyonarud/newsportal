# newsportal
учебный проект по созданию новостного портала на джанго


Работа в консоли:
Что вы должны сделать в консоли Django?
1.	Создать двух пользователей (с помощью метода User.objects.create_user('username')).
u1 = User.objects.create_user('Alyona', 'alyona@mail.ru', 'alyonapass')
u2 = User.objects.create_user('Alisa', 'alisa@mail.ru', 'alisapass')
2.	Создать два объекта модели Author, связанные с пользователями.
Author.objects.create(authorUser = u1)
Author.objects.create(authorUser = u2)
3.	Добавить 4 категории в модель Category.
Category.objects.create(name = 'IT')
Category.objects.create(name = 'POLIT')
Category.objects.create(name = 'SOC')
Category.objects.create(name = 'HIST')
4.	Добавить 2 статьи и 1 новость.

Post.objects.create(author= Author.objects.get(id = 1), categoryType='AR', title='Руководство по проектированию реляционных баз данных', text='1. Вступление. Если вы собираетесь создавать собственные базы данных, то неплохо было бы придерживаться правил проектирования баз данных, так как это обеспечит долговременную целостность и простоту обслуживания ваших данных. Данное руководство расскажет вам что представляют из себя базы данных и как спроектировать базу данных, которая подчиняется правилам проектирования реляционных баз данных.Базы данных – это программы, которые позволяют сохранять и получать большие объемы связанной информации. Базы данных состоят из таблиц, которые содержат информацию. Когда вы создаете базу данных необходимо подумать о том, какие таблицы вам нужно создать и какие связи существуют между информацией в таблицах. Иначе говоря, вам нужно подумать о проекте вашей базы данных. Хороший проект базы данных, как было сказано ранее, обеспечит целостность данных и простоту их обслуживания.')

Post.objects.create(author= Author.objects.get(id = 2), categoryType='AR', title= 'Социология управления', text= 'Социология управления — отрасль социологической науки, изучающая механизмы социального управления и управленческие процессы в больших и малых социальных системах с учетом социокультурных и социально-экономических характеристик данных систем (общества, организаций). Социология управления - сфера научных социологических исследований, содержащая в себе исследование социальных механизмов и способов управленческого воздействия на общество, его отдельные сферы (экономическую, социальную, политическую, духовную), социальные группы и организации, на сознание и поведение людей. Научная специальность по которой выполняется подготовка научных работников (кандидатов и докторов социологических наук).')

Post.objects.create(author= Author.objects.get(id = 1), categoryType='NW', title=' Из Алма-Аты возобновили пассажирские рейсы с 13 января', text= 'В связи со стабилизацией ситуации в Казахстане мероприятия по вывозу граждан России самолетами Минобороны завершаются, говорится в Telegram-канале ДСКЦ МИД РФ.')
5.	Присвоить им категории (как минимум в одной статье/новости должно быть не меньше 2 категорий).

# присвоили статье 1 категорию IT:
Post.objects.get(id = 1).postCategory.add(Category.objects.get(id = 1))

# присвоили статье 2 категорию SOC
Post.objects.get(id = 2).postCategory.add(Category.objects.get(id = 3))

# присвоили новости 3 категории SOC, POLIT
Post.objects.get(id = 3).postCategory.add(Category.objects.get(id = 3))
Post.objects.get(id = 3).postCategory.add(Category.objects.get(id = 2))

6.	Создать как минимум 4 комментария к разным объектам модели Post (в каждом объекте должен быть как минимум один комментарий).
Comment.objects.create(commentPost= Post.objects.get(id = 1), commentUser = Author.objects.get(id = 2).authorUser, text = 'Интересная статья, спасибо!')
Comment.objects.create(commentPost= Post.objects.get(id = 1), commentUser = Author.objects.get(id = 1).authorUser, text = 'Спасибо за отзыв!')
Comment.objects.create(commentPost= Post.objects.get(id = 2), commentUser = Author.objects.get(id = 1).authorUser, text = 'Интересная статья, жду продолжение!')
Comment.objects.create(commentPost= Post.objects.get(id = 3), commentUser = Author.objects.get(id = 2).authorUser, text = 'Ура, лечу')


7.	Применяя функции like() и dislike() к статьям/новостям и комментариям, скорректировать рейтинги этих объектов.
Comment.objects.get(id = 1).like()
Comment.objects.get(id = 1).rating
Post.objects.get(id = 1).like()
Post.objects.get(id = 1).dislike()
Post.objects.get(id = 1).dislike()
Post.objects.get(id = 1).dislike()
Post.objects.get(id = 1).rating


Post.objects.get(id = 2).like()
Post.objects.get(id = 2).like()
Post.objects.get(id = 2).like()
Post.objects.get(id = 2).rating

Post.objects.get(id = 3).like()
Post.objects.get(id = 3).like()
Post.objects.get(id = 3).like()
Post.objects.get(id = 3).like()
Post.objects.get(id = 3).like()
Post.objects.get(id = 3).dislike()
Post.objects.get(id = 3).rating


Comment.objects.get(id = 2).like()
Comment.objects.get(id = 2).rating

Comment.objects.get(id = 3).like()
Comment.objects.get(id = 3).rating

Comment.objects.get(id = 4).dislike()
Comment.objects.get(id = 4).rating
