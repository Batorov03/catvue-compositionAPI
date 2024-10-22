<template>
  <div>
    <header class="header">
      <div class="overlay"></div>
      <div class="container">
        <div class="header__block">
          <div class="header__nav">
            <div href="">
              <img
                class="logo-img"
                src="./images/logo.svg"
                alt="логотип сайта"
              />
            </div>
            <ul class="menu">
              <li class="menu__item">Main</li>
              <li class="menu__item">Gallery</li>
              <li class="menu__item">News</li>
              <li class="menu__item">Profile</li>
            </ul>
          </div>

          <div class="header__phone">
            <a href="tel: 544349000000" class="phone">+544 3490 00000</a>
            <span class="phone__title">Звони скорее!</span>
            <span class="header__title">Найдено 349 котов</span>
          </div>
        </div>
      </div>
    </header>
    <section class="section">
      <div class="container">
        <div class="section__sort">
          <span> Сортировать по: </span>
          <span class="span">
            Цена
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="15"
              height="15"
              viewBox="0 0 15 15"
              fill="none"
            >
              <g clip-path="url(#clip0_5_152)">
                <path
                  d="M8.0853 11.6669L14.7604 4.99166C14.9149 4.83727 15 4.63118 15 4.41142C15 4.19167 14.9149 3.98557 14.7604 3.83118L14.2689 3.3396C13.9487 3.01973 13.4282 3.01973 13.1084 3.3396L7.50311 8.94492L1.89157 3.33338C1.73706 3.17899 1.53109 3.09375 1.31146 3.09375C1.09158 3.09375 0.885606 3.17899 0.730973 3.33338L0.239635 3.82496C0.0851249 3.97947 3.76698e-06 4.18545 3.75737e-06 4.4052C3.74777e-06 4.62496 0.0851249 4.83105 0.239635 4.98544L6.9208 11.6669C7.0758 11.8216 7.28275 11.9066 7.50275 11.9061C7.7236 11.9066 7.93042 11.8216 8.0853 11.6669Z"
                  fill="black"
                />
              </g>
              <defs>
                <clipPath id="clip0_5_152">
                  <rect
                    width="15"
                    height="15"
                    fill="white"
                    transform="translate(15) rotate(90)"
                  />
                </clipPath>
              </defs>
            </svg>
          </span>
          <span class="span">
            Возраст
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="15"
              height="15"
              viewBox="0 0 15 15"
              fill="none"
            >
              <g clip-path="url(#clip0_5_152)">
                <path
                  d="M8.0853 11.6669L14.7604 4.99166C14.9149 4.83727 15 4.63118 15 4.41142C15 4.19167 14.9149 3.98557 14.7604 3.83118L14.2689 3.3396C13.9487 3.01973 13.4282 3.01973 13.1084 3.3396L7.50311 8.94492L1.89157 3.33338C1.73706 3.17899 1.53109 3.09375 1.31146 3.09375C1.09158 3.09375 0.885606 3.17899 0.730973 3.33338L0.239635 3.82496C0.0851249 3.97947 3.76698e-06 4.18545 3.75737e-06 4.4052C3.74777e-06 4.62496 0.0851249 4.83105 0.239635 4.98544L6.9208 11.6669C7.0758 11.8216 7.28275 11.9066 7.50275 11.9061C7.7236 11.9066 7.93042 11.8216 8.0853 11.6669Z"
                  fill="black"
                />
              </g>
              <defs>
                <clipPath id="clip0_5_152">
                  <rect
                    width="15"
                    height="15"
                    fill="white"
                    transform="translate(15) rotate(90)"
                  />
                </clipPath>
              </defs>
            </svg>
          </span>
        </div>
        <div class="section__product">
          <div class="cards">
            <div
              class="card"
              v-for="(product, index) in products"
              :key="product.id"
            >
              <div class="card__item">
                <img class="product-img" src="./images/kot-1.png" alt="" />
              </div>
              <h3 class="card__name">{{ product.name }}</h3>
              <div class="description__block">
                <div class="before">Коричневый окрас</div>
                <div class="flex-col">
                  <div class="black">3 года</div>
                  <div>Возраст</div>
                </div>
              </div>
              <div class="details">
                <div class="things">шт:</div>

                <div class="counter-wrapper">
                  <div class="items__control" @click="decrement(index)">-</div>
                  <div class="items__current" data-counter>
                    {{ product.quantity }}
                  </div>
                  <div class="items__control" @click="increment(index)">+</div>
                </div>
                <div class="price">
                  <div class="price__currency">{{ product.price }}₽</div>
                </div>
              </div>
              <button @click="addToCart(product)" class="section__button">
                Купить
              </button>
            </div>
          </div>

          <div class="col-md-4">
            <!-- Корзина -->
            <div class="card">
              <div class="card-body">
                <h5 class="card-title">Ваш заказ</h5>
                <hr />
                <div data-cart-empty class="alert alert-secondary" role="alert">
                  Корзина пуста
                </div>

                <!-- cart-wrapper -->

                <div class="cart-wrapper" v-if="cart.length > 0">
                  <div class="card__new" v-for="item in cart" :key="item.id">
                    <div class="card__item-cat">
                      <img class="product-png" src="#" alt="" />
                      <div class="d">
                        <h3 class="card__name-cat">{{ item.name }}</h3>
                        <div class="details__cat">
                          <div class="things-cat"></div>

                          <div class="counter-wrapper">
                            <div
                              class="items__control"
                              @click="decrementCart(item)"
                            >
                              -
                            </div>
                            <div class="items__current">
                              {{ item.quantity }}
                            </div>
                            <div
                              class="items__control"
                              @click="incrementCart(item)"
                            >
                              +
                            </div>
                          </div>

                          <div class="price">
                            <div class="price__currency">
                              {{ item.price }} ₽
                            </div>
                          </div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <!-- // cart-wrapper
	
							<!- Стоимость заказа -->
                <div class="cart-total">
                  <p data-cart-delivery class="none">
                    <span class="h5">Доставка:</span>
                    <span class="delivery-cost"></span>
                    <span class="small">Бесплатно при заказе от 600р </span>
                  </p>
                  <p>
                    <span class="h5">Итого:</span>
                    <span class="total-price"> {{ totalPrice }}</span>
                    <span class="rouble">₽</span>
                  </p>
                </div>
                <!-- // Стоимость заказа -->
              </div>

              <!-- Оформить заказ -->
              <div id="order-form" class="card-body border-top none">
                <h5 class="card-title">Оформить заказ</h5>
                <form>
                  <div class="form-group">
                    <input
                      type="text"
                      class="form-control"
                      placeholder="Ваш номер телефона"
                    />
                  </div>
                  <button type="submit" class="btn btn-primary">
                    Заказать
                  </button>
                </form>
              </div>
              <!-- // Оформить заказ -->
            </div>

            <!-- // Корзина -->
          </div>
        </div>

        <div class="about">
          <button class="button">Показать еще</button>
          <div class="svg">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="18"
              height="18"
              viewBox="0 0 18 18"
              fill="none"
            >
              <g clip-path="url(#clip0_201_1)">
                <path
                  d="M8.29764 3.99939L0.287559 12.0096C0.102145 12.1949 -8.06437e-08 12.4422 -6.91167e-08 12.7059C-5.75898e-08 12.9696 0.102145 13.2169 0.287559 13.4022L0.87731 13.9921C1.2616 14.3759 1.88618 14.3759 2.26988 13.9921L8.99627 7.2657L15.7301 13.9996C15.9155 14.1848 16.1627 14.2871 16.4263 14.2871C16.6901 14.2871 16.9373 14.1848 17.1228 13.9995L17.7124 13.4097C17.8979 13.2242 18 12.9771 18 12.7134C18 12.4497 17.8979 12.2023 17.7124 12.0171L9.69504 3.99939C9.50904 3.81368 9.26071 3.71168 8.99671 3.71227C8.73169 3.71168 8.48349 3.81368 8.29764 3.99939Z"
                  fill="white"
                />
              </g>
              <defs>
                <clipPath id="clip0_201_1">
                  <rect
                    width="18"
                    height="18"
                    fill="white"
                    transform="translate(0 18) rotate(-90)"
                  />
                </clipPath>
              </defs>
            </svg>
          </div>
        </div>
      </div>
      <div></div>
    </section>
  </div>
</template>

<script>
  import { ref, computed } from "vue"

  export default {
    name: "App",
    components: {
      // HelloWorld
    },
    setup() {
      // Список продуктов
      const products = ref([
        {
          id: 1,
          name: "Товар 1",
          price: 100,
          quantity: 1,
        },
        {
          id: 2,
          name: "Товар 2",
          price: 200,
          quantity: 1,
        },
        {
          id: 3,
          name: "Товар 3",
          price: 300,
          quantity: 1,
        },
      ])

      // Корзина
      const cart = ref([])

      // Общая стоимость корзины
      const totalPrice = computed(() => {
        return cart.value.reduce(
          (sum, item) => sum + item.price * item.quantity,
          0
        )
      })

      // Увеличение количества товара на карточке
      const increment = (index) => {
        products.value[index].quantity++
      }

      // Уменьшение количества товара на карточке
      const decrement = (index) => {
        if (products.value[index].quantity > 1) {
          products.value[index].quantity--
        }
      }

      // Добавление товара в корзину
      const addToCart = (product) => {
        const existingProduct = cart.value.find(
          (item) => item.id === product.id
        )
        if (existingProduct) {
          existingProduct.quantity += product.quantity // Увеличиваем количество в корзине
        } else {
          cart.value.push({ ...product })
        }
        product.quantity = 1 // Обнуляем количество товара на карточке после добавления в корзину
      }

      // Увеличение количества товара в корзине
      const incrementCart = (item) => {
        item.quantity++
      }

      // Уменьшение количества товара в корзине
      const decrementCart = (item) => {
        if (item.quantity > 1) {
          item.quantity--
        }
      }

      return {
        products,
        cart,
        totalPrice,
        increment,
        decrement,
        addToCart,
        incrementCart,
        decrementCart,
      }
    },
  }
</script>

<style>
  @import url(./css/style.css);
  @import url(./css/normalize.css);
</style>
