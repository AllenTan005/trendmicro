

<template>
  <Teleport to="#teleport">
    <div>


      <div v-if="open" class="modal-bg">
        <div class="modal">
          <input type="text" v-model="newFolder"
            class="bg-gray-50 border w-[100%] mb-5 border-gray-300 text-gray-900 sm:text-sm rounded-lg focus:ring-cyan-600 focus:border-cyan-600 block pl-10 p-2.5" />
          <div class=" flex justify-between">
            <button @click="addNew()" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">Add
              new
              item</button>
            <button @click="open = false"
              class="bg-red-500 hover:bg-red-700 text-white font-bold py-2 px-4 rounded">Close</button>
          </div>
        </div>
      </div>
    </div>
  </Teleport>


  <body class="overflow-hidden text-gray-800">
    <!-- 
    <div id="toast-undo"
      class="drop-shadow-2xl absolute mx-auto left-0 right-0 bottom-24 z-10 flex items-center p-4 max-w-xs text-gray-500 bg-white rounded-lg shadow dark:text-gray-400 dark:bg-gray-800"
      role="alert">
      <div class="text-sm font-normal">
        Folder created.
      </div>
      <div class="flex items-center ml-auto space-x-2">
        <a class="text-sm font-medium text-cyan-600 p-1.5 hover:bg-cyan-100 rounded-lg dark:text-cyan-500 dark:hover:bg-gray-700"
          href="#">Undo</a>
        <button type="button"
          class="bg-white text-gray-400 hover:text-gray-900 rounded-lg focus:ring-2 focus:ring-gray-300 p-1.5 hover:bg-gray-100 inline-flex h-8 w-8 dark:text-gray-500 dark:hover:text-white dark:bg-gray-800 dark:hover:bg-gray-700"
          data-dismiss-target="#toast-undo" aria-label="Close">
          <span class="sr-only">Close</span>
          <svg aria-hidden="true" class="w-5 h-5" fill="currentColor" viewBox="0 0 20 20"
            xmlns="http://www.w3.org/2000/svg">
            <path fill-rule="evenodd"
              d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z"
              clip-rule="evenodd"></path>
          </svg>
        </button>
      </div>
    </div> -->
    <div id="header" class="z-20 flex items-center bg-cyan-700 fixed top-0 w-full shadow-md">
      <div class="px-16 left-nav py-4 w-1/5 text-white font-bold text-2xl tracking-wide">TrendMicro</div>
      <div
        class="flex justify-between right-nav text-gray-500 items-center px-8 py-2 w-4/5 text-white float-right font-bold">
        <div class="relative flex items-center">
          <i class="text-2xl fa fa-bars mr-4 text-white" id="hide"></i>

          <!-- <input type="text" class="rounded-lg px-5 py-3 bg-white hover:bg-white" placeholder="Search">
			  <i class="text-gray-500 fa fa-times absolute right-0 p-6" aria-hidden="true"></i> -->
          <span class="flex items-center relative">
            <i class="text-xl fa fa-search text-cyan-700 absolute left-3 active:bg-white" aria-hidden="true"></i>
            <input type="text" name="email" id="topbar-search"
              class="bg-gray-50 border border-gray-300 text-gray-900 sm:text-sm rounded-lg focus:ring-cyan-600 focus:border-cyan-600 block w-full pl-10 p-2.5"
              placeholder="Search111" v-model="searchItem">
          </span>
        </div>
        <div>
          <div class="flex items-center">
            <span><i class="relative text-2xl fa fa-list mr-4 text-white " data-modal-toggle="extralarge-modal"
                aria-hidden="true"></i></span>
            <span><i class="relative text-2xl fa fa-wrench mr-4 text-white " aria-hidden="true"></i></span>
            <div id="notification">
              <span><i class="text-2xl fa fa-bell mr-4 text-white" aria-hidden="true"></i></span>
            </div>
            <span class="mr-6"><i class="text-2xl fa fa-cog mr-4 text-white" aria-hidden="true"></i></span>
            <div class="flex items-center justify-center mr-6">
              <span class="text-base text-gray text-gray-500 z-30">N</span>
              <div id="setting" class="w-10 h-10 bg-white absolute rounded-full"></div>
            </div>
          </div>
          <!-- <div class="w-0 h-0 mx-auto
				border-l-[10px] border-l-transparent
				border-b-[12px] border-white
				border-r-[10px] border-r-transparent
				 "></div> -->

          <div id="setting_sub"
            class="hidden z-40 absolute right-0 mt-3 mx-8 bg-white shadow-lg w-60 p-4 rounded-lg text-center text-cyan-700">
            <div class="flex items-center">
              <div class="flex items-center p-4">
                <div class="flex items-center justify-center mr-2">
                  <span class="text-base text-gray text-white z-30">N</span>
                  <div class="w-10 h-10 border bg-cyan-700 absolute rounded-full"></div>
                </div>
              </div>
              <div>Name(EXT-TW)</div>
            </div>
            <hr class="mt-2">
            <div class="text-left">
              <ul class="mt-2 flex items-center">
                <li class="text-gray-500 w-1/2">Font-size</li>
                <div class="w-1/2 flex items-center">
                  <button class="mr-1"><i class="text-2xl fa fa-minus-circle" aria-hidden="true"></i></button>
                  <button class="mr-1"><i class="text-2xl fa fa-plus-circle" aria-hidden="true"></i></button>
                  <button
                    class="cyan_color rounded px-2 bg-gray-400 hover:bg-gray-500 text-white text-sm">reset</button>
                </div>
              </ul>
              <hr class="mt-2">
              <ul class="mt-2 flex">
                <li class="text-gray-500 w-1/2">Theme</li>
                <div class="w-1/2 flex items-center">
                  <button class="cyan_color rounded-xl w-5 h-5 bg-cyan-700 mr-1"></button>
                  <button id="red" class="rounded-xl w-5 h-5 bg-red-700 mr-1"></button>
                  <button
                    class="cyan_color rounded px-2 bg-gray-400 hover:bg-gray-500 text-white text-sm">reset</button>
                </div>
              </ul>
              <hr class="mt-2">
              <ul class="mt-2">
                <!-- <li class="text-gray-500">Language</li> -->
                <select id="countries"
                  class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500">
                  <option selected class="text-gray-500">Language</option>
                  <option value="US">English</option>
                  <option value="CA">日本語</option>
                </select>
              </ul>
              <hr class="mt-2">
              <ul class="mt-2">
                <li class="text-gray-500">Shared information</li>
                <img src="https://ithelp.ithome.com.tw/upload/images/20201009/20107810EsXFQBVgNo.png" alt="">
              </ul>
              <hr class="mt-2">
              <ul class="mt-2">
                <li class="text-gray-500">Setting</li>
              </ul>
              <hr class="mt-2">
              <ul class="mt-2">
                <li class="text-gray-500">Files</li>
              </ul>
            </div>
            <hr class="mt-2">
            <div class="mt-2">
              <button class="border border-cyan-700 rounded py-2 px-4">Sign Out</button>
            </div>
          </div>

          <!-- notification sub -->
          <div id="notification_content"
            class="hidden z-50 absolute right-24 mt-3 mx-8 bg-white shadow-lg w-96 rounded-lg text-center text-cyan-700">
            <div class="flex items-center justify-center bg-gray-100 px-4 py-2 rounded-t-lg">
              <div>Notification</div>
            </div>
            <hr>
            <div id="notification_sub">
            </div>
            <div class="flex items-center justify-center hover:bg-cyan-700 hover:text-white px-4 py-2 rounded-b-lg">
              <i class="fa fa-eye mr-2" aria-hidden="true"></i>
              <div>View all</div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="flex pt-16 mt-1">
      <div class="overflow-auto relative h-screen shadow-md w-1/5 left-nav">
        <div class="flex flex-col overflow-y-scroll h-2/3 text-sm">
          <a class="hover:bg-gray-100 pl-6 pr-12 py-2 block border-gray-300 mt-6" href="#">
            <i class="text-gray-500 text-xl fa fa-cloud mr-2" aria-hidden="true"></i>
            <span class="text-base font-bold">Name(EXT-TW)</span>
          </a>
          <a class="hover:bg-gray-100 pl-8 py-1.5 block border-gray-300" href="#">
            <span>
              <i class="text-gray-500 text-xl fa fa-angle-right w-5 mr-1 text-center" aria-hidden="true"></i>
              <i class=" text-xl fa fa-folder text-gray-500 mr-2" aria-hidden="true"></i>
            </span>
            20220126-2
          </a>
          <div class="flex flex-col">
            <a class="hover:bg-gray-100 pl-8 py-1.5 block border-gray-300" href="#">
              <span>
                <i class="text-gray-500 text-xl fa fa-angle-down w-5 mr-1 text-center" aria-hidden="true"></i>
                <i class="text-gray-500 text-xl fa fa-folder-open mr-2" aria-hidden="true"></i>
              </span>
              test@trend.c...
            </a>
            <a class="hover:bg-gray-100 pl-12 py-2 block border-gray-300" href="#">
              <span>
                <i class="text-gray-500 text-xl fa fa-angle-right w-5 mr-1 text-center" aria-hidden="true"></i>
                <i class="text-gray-500 text-xl fa fa-folder mr-2" aria-hidden="true"></i>
              </span>
              sub_01_case...
            </a>
            <a class="bg-blue-200 pl-12 py-2 block border-gray-300" href="#">
              <span>
                <i class="text-gray-500 text-xl fa fa-angle-down w-5 mr-1 text-center" aria-hidden="true"></i>
                <i class="text-gray-500 text-xl fa fa-folder-open mr-2" aria-hidden="true"></i>
              </span>
              sub_02_case...
            </a>
          </div>
          <a class="hover:bg-gray-100 pl-8 py-1.5 block border-gray-300" href="#">
            <span>
              <i class="text-gray-500 text-xl fa fa-angle-right w-5 mr-1 text-center" aria-hidden="true"></i>
              <i class="text-gray-500 text-xl fa fa-folder mr-2" aria-hidden="true"></i>
            </span>
            2022_end...
          </a>
          <a class="hover:bg-gray-100 pl-6 pr-12 py-2 block border-gray-300 mt-2" href="#">
            <i class="text-gray-500 text-xl fa fa-star mr-2" aria-hidden="true"></i>
            <span class="text-base font-bold">Favorities</span>
          </a>
          <a class="hover:bg-gray-100 pl-6 pr-12 py-2 block border-gray-300 mt-2" href="#">
            <i class="text-gray-500 text-xl fa fa-trash mr-2" aria-hidden="true"></i>
            <span class="text-base font-bold">Rubbish bin</span>
          </a>
        </div>
        <hr>
        <div class="py-5 fixed bottom-0 w-1/5 border-t px-8 bg-gray-100">
          <div class="mb-4 text-xl font-bold">Account Usage</div>
          <div class="bg-gray-300 h-2 rounded">
            <div class="bg-gray-700 h-2 w-1/3 rounded"></div>
          </div>
          <div class="mt-4 tracking-wide text-sm"><span class="text-sky-700">1.29 MB </span> used out of 2MB </div>
        </div>
      </div>
      <!-- <div class="w-4/5 right-nav -z-10"> -->
      <div class="w-4/5 right-nav">
        <div class="relative flex items-center mx-8">
          <div class="list flex items-center">
            <!-- <button id="dp_btn" class="flex items-center justify-center my-4 hover:bg-cyan-500 hover:text-white py-2 px-4 rounded-lg text-center text-cyan-500" data-modal-toggle="defaultModal"> -->
            <button id="dp_btn"
              class="flex items-center justify-center my-4 hover:bg-cyan-500 hover:text-white py-2 px-4 rounded-lg text-center text-cyan-500"
              data-modal-toggle="small-modal" @click="open = true">
              <i class="text-2xl fa fa-plus mr-2" aria-hidden="true"></i>
              <span>New Folder</span>
            </button>
            <button id="dp_btn"
              class="flex items-center justify-center my-4 hover:bg-cyan-500 hover:text-white py-2 px-4 rounded-lg text-center text-cyan-500">
              <i class="text-2xl fas fa-upload mr-2" aria-hidden="true"></i>
              <span>Upload</span>
            </button>
            <button @click="deleteItem(this.selectedCustomers)"
              class="bg-red-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">Delete</button>

            <!-- Link modal -->
            <div id="extralarge-modal" tabindex="-1"
              class="hidden overflow-y-auto overflow-x-hidden fixed top-0 right-0 left-0 z-50 w-full md:inset-0 h-modal md:h-full">
              <div class="relative p-4 w-full max-w-7xl h-full md:h-auto">
                <!-- Modal content -->
                <div class="relative bg-white rounded-lg shadow dark:bg-gray-700">
                  <!-- Modal header -->
                  <div class="flex justify-between items-center p-5 rounded-t border-b dark:border-gray-600">
                    <h3 class="text-xl font-medium text-gray-900 dark:text-white">
                      Powerbox List
                    </h3>
                    <button type="button"
                      class="text-gray-400 bg-transparent hover:bg-gray-200 hover:text-gray-900 rounded-lg text-sm p-1.5 ml-auto inline-flex items-center dark:hover:bg-gray-600 dark:hover:text-white"
                      data-modal-toggle="extralarge-modal">
                      <svg aria-hidden="true" class="w-5 h-5" fill="currentColor" viewBox="0 0 20 20"
                        xmlns="http://www.w3.org/2000/svg">
                        <path fill-rule="evenodd"
                          d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z"
                          clip-rule="evenodd"></path>
                      </svg>
                      <span class="sr-only">Close modal</span>
                    </button>
                  </div>
                  <!-- Modal body -->
                  <div class="p-6 space-y-6">
                    <div class="mb-4 border-b border-gray-200 dark:border-gray-700">
                      <ul class="flex flex-wrap -mb-px text-sm font-medium text-center" id="myTab"
                        data-tabs-toggle="#myTabContent" role="tablist">
                        <li class="mr-2" role="presentation">
                          <button class="inline-block p-4 rounded-t-lg border-b-2" id="profile-tab"
                            data-tabs-target="#profile" type="button" role="tab" aria-controls="profile"
                            aria-selected="false">FTP</button>
                        </li>
                        <li class="mr-2" role="presentation">
                          <button
                            class="inline-block p-4 rounded-t-lg border-b-2 border-transparent hover:text-gray-600 hover:border-gray-300 dark:hover:text-gray-300"
                            id="dashboard-tab" data-tabs-target="#dashboard" type="button" role="tab"
                            aria-controls="dashboard" aria-selected="false">Shared Folder</button>
                        </li>
                        <li class="mr-2" role="presentation">
                          <button
                            class="inline-block p-4 rounded-t-lg border-b-2 border-transparent hover:text-gray-600 hover:border-gray-300 dark:hover:text-gray-300"
                            id="settings-tab" data-tabs-target="#settings" type="button" role="tab"
                            aria-controls="settings" aria-selected="false">Shared File</button>
                        </li>
                        <li role="presentation">
                          <button
                            class="inline-block p-4 rounded-t-lg border-b-2 border-transparent hover:text-gray-600 hover:border-gray-300 dark:hover:text-gray-300"
                            id="contacts-tab" data-tabs-target="#contacts" type="button" role="tab"
                            aria-controls="contacts" aria-selected="false">External Upload</button>
                        </li>
                      </ul>
                    </div>
                    <div id="myTabContent">
                      <div class="hidden p-4 bg-gray-50 rounded-lg dark:bg-gray-800" id="profile" role="tabpanel"
                        aria-labelledby="profile-tab">
                        <!-- <p class="text-sm text-gray-500 dark:text-gray-400">This is 1some placeholder content the <strong class="font-medium text-gray-800 dark:text-white">Profile tab's associated content</strong>. Clicking another tab will toggle the visibility of this one for the next. The tab JavaScript swaps classes to control the content visibility and styling.</p> -->
                        <div id="ftp_demo" class="overflow-x-auto relative tab_demo">
                        </div>
                      </div>
                      <div class="hidden p-4 bg-gray-50 rounded-lg dark:bg-gray-800" id="dashboard" role="tabpanel"
                        aria-labelledby="dashboard-tab">
                        <div class="overflow-x-auto relative tab_demo">
                        </div>
                      </div>
                      <div class="hidden p-4 bg-gray-50 rounded-lg dark:bg-gray-800" id="settings" role="tabpanel"
                        aria-labelledby="settings-tab">
                        <div class="overflow-x-auto relative tab_demo">
                        </div>
                      </div>
                      <div class="hidden p-4 bg-gray-50 rounded-lg dark:bg-gray-800" id="contacts" role="tabpanel"
                        aria-labelledby="contacts-tab">
                        <!-- <p class="text-sm text-gray-500 dark:text-gray-400">This is 4some placeholder content the <strong class="font-medium text-gray-800 dark:text-white">Contacts tab's associated content</strong>. Clicking another tab will toggle the visibility of this one for the next. The tab JavaScript swaps classes to control the content visibility and styling.</p> -->
                        <div class="overflow-x-auto relative tab_demo">
                        </div>
                      </div>
                    </div>
                  </div>
                  <!-- Modal footer -->
                  <!-- <div class="flex items-center p-6 space-x-2 rounded-b border-t border-gray-200 dark:border-gray-600">
									<button data-modal-toggle="extralarge-modal" type="button" class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">I accept2</button>
									<button data-modal-toggle="extralarge-modal" type="button" class="text-gray-500 bg-white hover:bg-gray-100 focus:ring-4 focus:outline-none focus:ring-gray-200 rounded-lg border border-gray-200 text-sm font-medium px-5 py-2.5 hover:text-gray-900 focus:z-10 dark:bg-gray-700 dark:text-gray-300 dark:border-gray-500 dark:hover:text-white dark:hover:bg-gray-600 dark:focus:ring-gray-600">Decline</button>
								</div> -->
                </div>
              </div>
            </div>

            <!-- Small modal create -->
            <!-- Small Modal -->
            <div id="small-modal" tabindex="-1"
              class="hidden overflow-y-auto overflow-x-hidden fixed top-0 right-0 left-0 z-50 w-full md:inset-0 h-modal md:h-full">
              <div class="relative p-4 w-full max-w-md h-full md:h-auto">
                <!-- Modal content -->
                <div class="relative bg-white rounded-lg shadow dark:bg-gray-700">
                  <!-- Modal header -->
                  <div class="flex justify-between items-center p-5 rounded-t border-b dark:border-gray-600">
                    <h3 class="text-xl font-medium text-gray-900 dark:text-white">
                      New Folder
                    </h3>
                    <button type="button"
                      class="text-gray-400 bg-transparent hover:bg-gray-200 hover:text-gray-900 rounded-lg text-sm p-1.5 ml-auto inline-flex items-center dark:hover:bg-gray-600 dark:hover:text-white"
                      data-modal-toggle="small-modal">
                      <svg aria-hidden="true" class="w-5 h-5" fill="currentColor" viewBox="0 0 20 20"
                        xmlns="http://www.w3.org/2000/svg">
                        <path fill-rule="evenodd"
                          d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z"
                          clip-rule="evenodd"></path>
                      </svg>
                      <span class="sr-only">Close modal</span>
                    </button>
                  </div>
                  <!-- Modal body -->
                  <div class="p-6 space-y-6">
                    <!-- <p class="text-base leading-relaxed text-gray-500 dark:text-gray-400">
										test With less than a month to go before the European Union enacts new consumer privacy laws for its citizens, companies around the world are updating their terms of service agreements to comply.
									</p> -->
                    <form class="space-y-6" action="#">
                      <div>
                        <label for="text" class="block mb-2 text-sm font-medium text-gray-900 dark:text-gray-300">File
                          Name</label>
                        <input type="text" name="text" id="text"
                          class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-600 dark:border-gray-500 dark:placeholder-gray-400 dark:text-white"
                          placeholder="please enter filename" required>
                      </div>
                      <button type="submit"
                        class="w-full text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">Create</button>
                    </form>
                  </div>
                  <!-- Modal footer -->
                  <!-- <div class="flex items-center p-6 space-x-2 rounded-b border-t border-gray-200 dark:border-gray-600">
									<button data-modal-toggle="small-modal" type="button" class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">Save</button>
									<button data-modal-toggle="small-modal" type="button" class="text-gray-500 bg-white hover:bg-gray-100 focus:ring-4 focus:outline-none focus:ring-gray-200 rounded-lg border border-gray-200 text-sm font-medium px-5 py-2.5 hover:text-gray-900 focus:z-10 dark:bg-gray-700 dark:text-gray-300 dark:border-gray-500 dark:hover:text-white dark:hover:bg-gray-600 dark:focus:ring-gray-600">Cancel</button>
								</div> -->
                </div>
              </div>
            </div>

            <!-- Delete modal -->
            <div id="popup-modal" tabindex="-1"
              class="hidden overflow-y-auto overflow-x-hidden fixed top-0 right-0 left-0 z-50 md:inset-0 h-modal md:h-full">
              <div class="relative p-4 w-full max-w-md h-full md:h-auto">
                <div class="relative bg-white rounded-lg shadow dark:bg-gray-700">
                  <button type="button"
                    class="absolute top-3 right-2.5 text-gray-400 bg-transparent hover:bg-gray-200 hover:text-gray-900 rounded-lg text-sm p-1.5 ml-auto inline-flex items-center dark:hover:bg-gray-800 dark:hover:text-white"
                    data-modal-toggle="popup-modal">
                    <svg aria-hidden="true" class="w-5 h-5" fill="currentColor" viewBox="0 0 20 20"
                      xmlns="http://www.w3.org/2000/svg">
                      <path fill-rule="evenodd"
                        d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z"
                        clip-rule="evenodd"></path>
                    </svg>
                    <span class="sr-only">Close modal</span>
                  </button>
                  <div class="p-6 text-center">
                    <svg aria-hidden="true" class="mx-auto mb-4 w-14 h-14 text-gray-400 dark:text-gray-200" fill="none"
                      stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                        d="M12 8v4m0 4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z"></path>
                    </svg>
                    <h3 class="mb-5 text-lg font-normal text-gray-500 dark:text-gray-400">Are you sure you want to
                      delete this folder?</h3>
                    <button id="confirm_del" data-modal-toggle="popup-modal" type="button"
                      class="text-white bg-red-600 hover:bg-red-800 focus:ring-4 focus:outline-none focus:ring-red-300 dark:focus:ring-red-800 font-medium rounded-lg text-sm inline-flex items-center px-5 py-2.5 text-center mr-2">
                      Yes, I'm sure
                    </button>
                    <button data-modal-toggle="popup-modal" type="button"
                      class="text-gray-500 bg-white hover:bg-gray-100 focus:ring-4 focus:outline-none focus:ring-gray-200 rounded-lg border border-gray-200 text-sm font-medium px-5 py-2.5 hover:text-gray-900 focus:z-10 dark:bg-gray-700 dark:text-gray-300 dark:border-gray-500 dark:hover:text-white dark:hover:bg-gray-600 dark:focus:ring-gray-600">No,
                      cancel</button>
                  </div>
                </div>
              </div>
            </div>

            <!-- Delete toast -->
            <div id="toast-success"
              class="hidden absolute top-2 flex items-center p-4 mb-4 w-full max-w-xs text-gray-500 bg-white rounded-lg shadow dark:text-gray-400 dark:bg-gray-800"
              role="alert">
              <div
                class="inline-flex flex-shrink-0 justify-center items-center w-8 h-8 text-green-500 bg-green-100 rounded-lg dark:bg-green-800 dark:text-green-200">
                <svg aria-hidden="true" class="w-5 h-5" fill="currentColor" viewBox="0 0 20 20"
                  xmlns="http://www.w3.org/2000/svg">
                  <path fill-rule="evenodd"
                    d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z"
                    clip-rule="evenodd"></path>
                </svg>
                <span class="sr-only">Check icon</span>
              </div>
              <div class="ml-3 text-sm font-normal">Item deleted successfully.</div>
              <button type="button"
                class="ml-auto -mx-1.5 -my-1.5 bg-white text-gray-400 hover:text-gray-900 rounded-lg focus:ring-2 focus:ring-gray-300 p-1.5 hover:bg-gray-100 inline-flex h-8 w-8 dark:text-gray-500 dark:hover:text-white dark:bg-gray-800 dark:hover:bg-gray-700"
                data-dismiss-target="#toast-success" aria-label="Close">
                <span class="sr-only">Close</span>
                <svg aria-hidden="true" class="w-5 h-5" fill="currentColor" viewBox="0 0 20 20"
                  xmlns="http://www.w3.org/2000/svg">
                  <path fill-rule="evenodd"
                    d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z"
                    clip-rule="evenodd"></path>
                </svg>
              </button>
            </div>

            <!-- Main modal -->
            <div id="defaultModal" tabindex="-1" aria-hidden="true"
              class="hidden overflow-y-auto overflow-x-hidden fixed top-0 right-0 left-0 z-50 w-full md:inset-0 h-modal md:h-full">
              <div class="relative p-4 w-full max-w-xl h-full md:h-auto">
                <!-- Modal content -->
                <div class="relative bg-white rounded-lg shadow dark:bg-gray-700">
                  <!-- Modal header -->
                  <div class="flex justify-between items-start p-4 rounded-t border-b dark:border-gray-600">
                    <h3 class="text-xl font-semibold text-gray-900 dark:text-white">
                      New Folder
                    </h3>
                    <button type="button"
                      class="text-gray-400 bg-transparent hover:bg-gray-100 hover:text-gray-900 rounded-lg text-sm p-1.5 ml-auto inline-flex items-center dark:hover:bg-gray-600 dark:hover:text-white"
                      data-modal-toggle="defaultModal">
                      <svg aria-hidden="true" class="w-5 h-5" fill="currentColor" viewBox="0 0 20 20"
                        xmlns="http://www.w3.org/2000/svg">
                        <path fill-rule="evenodd"
                          d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z"
                          clip-rule="evenodd"></path>
                      </svg>
                      <span class="sr-only">Close modal</span>
                    </button>
                  </div>
                  <!-- Modal body -->
                  <div class="p-6 space-y-6">
                    <div>
                      <!-- <label for="default-input" class="block mb-2 text-sm font-medium text-gray-900 dark:text-gray-300">Default input</label> -->
                      <input name="filename" type="text" id="default-input"
                        class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-cyan-500 focus:border-cyan-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-cyan-500 dark:focus:border-cyan-500"
                        placeholder="Please enter a name for the new folder" value="popup">
                    </div>
                  </div>
                  <!-- Modal footer -->
                  <div class="flex items-center p-6 space-x-2 rounded-b border-t border-gray-200 dark:border-gray-600">
                    <!-- <button data-modal-toggle="defaultModal" type="button" class="text-gray-500 bg-white hover:bg-gray-100 focus:ring-4 focus:outline-none focus:ring-cyan-300 rounded-lg border border-gray-200 text-sm font-medium px-5 py-2.5 hover:text-gray-900 focus:z-10 dark:bg-gray-700 dark:text-gray-300 dark:border-cyan-700 dark:hover:text-white dark:hover:bg-gray-600 dark:focus:ring-gray-600">Cancel</button> -->
                    <button data-modal-toggle="defaultModal" id="addFile" type="submit"
                      class="text-white bg-cyan-700 hover:bg-cyan-800 focus:ring-4 focus:outline-none focus:ring-cyan-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center dark:bg-cyan-600 dark:hover:bg-cyan-700 dark:focus:ring-cyan-800">Create</button>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div id="" class="absolute top-2 left-0 flex items-center justify-between">
            <div class="hidden bg-white shadow-md p-4 pl-8 rounded-lg head_items">
              <span class="border-r border-gray-200 text-cyan-700"><span id="count"
                  class="text-cyan-500 text-bold px-2">0 </span>select items
                <i class="text-gray-500 fa fa-times p-2 selected_clear" aria-hidden="true"></i>
              </span>
              <button id="rename" data-tooltip-target="tooltip-bottom" data-tooltip-placement="bottom" type="button">
                <i class="w-16 text-2xl text-center fa fa-pencil text-cyan-500"></i>
              </button>
              <div id="tooltip-bottom" role="tooltip"
                class="inline-block absolute invisible py-1 px-2 text-sm font-medium text-white bg-gray-500 rounded-lg shadow-sm opacity-0 tooltip dark:bg-gray-700">
                rename
                <div class="tooltip-arrow" data-popper-arrow></div>
              </div>

              <i id="delFile" data-modal-toggle="popup-modal"
                class="w-16 text-2xl text-center fa fa-trash text-cyan-500"></i>
              <i class="w-16 text-2xl text-center fa fa-refresh text-cyan-500"></i>
              <i class="w-16 text-2xl text-center fa fa-arrows text-cyan-500"></i>
              <i class="w-16 text-2xl text-center fa fa-arrow-down text-cyan-500"></i>
              <i class="w-16 text-2xl text-center fa fa-list text-cyan-500"></i>
              <!-- <li>Download</li>
						<li>Share</li>
						<li>File Rename</li>
						<li>Preview</li>
						<li>Copy Url</li>
						<li>Delete</li>
						<li>More</li> -->
              <!-- Upload New Rename Delete Refresh Move Block -->
            </div>
          </div>
        </div>
        <hr>
        <div class="flex items-center p-2 mt-2 mx-8 border-cyan-700">
          <span>
            <i class="text-gray-500 text-xl mr-1 fa fa-cloud" aria-hidden="true"></i>
            <a class="hover:underline rounded-lg text-gray-500 text-sm text-center">test@trendmicro.com</a>
          </span>
          <i class="text-2xl fa fa-angle-right text-gray-500 mx-4" aria-hidden="true"></i>
          <span>
            <i class="text-gray-500 text-xl mr-1 fa fa-folder" aria-hidden="true"></i>
            <a class="hover:underline rounded-lg text-gray-500 text-sm text-center">test@trend.c...</a>
          </span>
          <i class="text-2xl fa fa-angle-right text-gray-500 mx-4" aria-hidden="true"></i>
          <span>
            <i class="text-gray-500 text-xl mr-1 fa fa-folder" aria-hidden="true"></i>
            <a class="hover:underline rounded-lg text-gray-500 text-sm text-center">sub_02_case_attachme</a>
          </span>
        </div>

        <ul id="contextMenu" class="hidden z-30 absolute bg-white py-2 px-4 right-4 top-10 rounded shadow-md w-52">
          <div class="p-2">Share</div>
          <div class="p-2">Download</div>
          <div class="p-2">SHA</div>
          <div class="p-2">Preview</div>
          <div class="p-2">Preview in New Tab</div>
          <div class="p-2">Copy URL</div>
        </ul>

        <!-- <div id="userTable"
          class="text-sm max-h-96 overflow-y-scroll border border-gray-200 mx-8 mt-2 rounded-lg text-gray-800">
          <ul class="z-10 sticky top-0 bg-white flex items-center p-2  border-b border-gray-200">
            <li class="w-1/12 flex items-center justify-center"><input id="selectall" type="checkbox"
                class="rounded-full w-5 h-5"></li>
            <li></li>
            <li class="w-1/12"></li>
            <li class="w-3/12 font-black">File Name</li>
            <li class="w-2/12 font-black">Type</li>
            <li class="w-2/12 font-black">Size</li>
            <li class="w-4/12 font-black">Last modified</li>
          </ul>
        </div> -->
        <div class="flex ">


        </div>


        <DataTable :value="users" class="p-datatable-customers" :rows="10" dataKey="id" :rowHover="true"
          v-model:selection="selectedCustomers" v-model:filters="filters" filterDisplay="menu" :loading="loading"
          responsiveLayout="scroll">

          <Column selectionMode="multiple" headerStyle="width: 3rem"></Column>
          <Column field="filename" header="filename" sortable style="min-width: 14rem">
          </Column>
          <Column field="type" header="type" sortable style="min-width: 14rem">
          </Column>
          <Column field="size" header="Size" sortable style="min-width: 14rem">
          </Column>
          <Column field="modify_time" header="last modifed" sortable style="min-width: 14rem">
          </Column>

        </DataTable>



        <div id="Linklist"
          class="hidden text-sm max-h-96 overflow-y-scroll border border-gray-200 mt-2 rounded-lg text-gray-800">
          <ul class="z-10 sticky top-0 bg-white flex items-center p-2  border-b border-gray-200">
            <li class="w-3/12 font-black">Create At</li>
            <li class="w-3/12 font-black">Expire At</li>
            <li class="w-2/12 font-black">Uploads</li>
            <li class="w-2/12 font-black">Mode</li>
            <li class="w-2/12 font-black">Folder</li>
          </ul>
        </div>

        <!-- new add btn 2 -->
        <!-- <button class="block text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800" type="button" data-modal-toggle="authentication-modal">
				Toggle modal
			</button> -->

        <!-- Main modal -->
        <!-- new add 2 -->
        <!-- <div id="authentication-modal" tabindex="-1" aria-hidden="true" class="hidden overflow-y-auto overflow-x-hidden fixed top-0 right-0 left-0 z-50 w-full md:inset-0 h-modal md:h-full"> -->
        <!-- <div class="relative p-4 w-full max-w-md h-full md:h-auto"> -->
        <!-- Modal content -->
        <!-- <div class="relative bg-white rounded-lg shadow dark:bg-gray-700">
						  <button type="button" class="absolute top-3 right-2.5 text-gray-400 bg-transparent hover:bg-gray-200 hover:text-gray-900 rounded-lg text-sm p-1.5 ml-auto inline-flex items-center dark:hover:bg-gray-800 dark:hover:text-white" data-modal-toggle="authentication-modal">
							  <svg aria-hidden="true" class="w-5 h-5" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><path fill-rule="evenodd" d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z" clip-rule="evenodd"></path></svg>
							  <span class="sr-only">Close modal</span>
						  </button>
						  <div class="py-6 px-6 lg:px-8">
							  <h3 class="mb-4 text-xl font-medium text-gray-900 dark:text-white">New Folder add</h3>
							  <form class="space-y-6" action="#">
								  <div>
									  <label for="text" class="block mb-2 text-sm font-medium text-gray-900 dark:text-gray-300">File Name</label>
									  <input type="text" name="text" id="text" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-600 dark:border-gray-500 dark:placeholder-gray-400 dark:text-white" placeholder="please enter filename" required>
								  </div>
								  <button type="submit" class="w-full text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">Create</button>
							  </form>
						  </div>
					  </div> -->
        <!-- </div> -->
        <!-- </div>  -->
      </div>
    </div>

  </body>

</template>

<script>
import DataTable from 'primevue/datatable';
import Column from 'primevue/column';
import { ref } from 'vue'

export default {

  components: {
    DataTable,
    Column
  },

  setup() {
    const open = ref(false)

    return {
      open
    }
  },

  data() {
    return {
      newFolder: '',
      selectedCustomers: null,
      searchUser: [],
      searchItem: '',
      users: [
        {
          id: 1,
          filename: "sub_01_case",
          type: "folder",
          size: "--",
          modify_time: "Oct7, 2022 2:36 PM(+08 00)",
          path: "Home",
          duration: "1s",
          status: "success"
        },
        {
          id: 2,
          filename: "Harry",
          type: "js",
          size: 0.62,
          modify_time: "Oct7, 2022 2:30 PM(+08 00)",
          path: "Home",
          duration: "1s",
          status: "success"
        },
        {
          id: 3,
          filename: "profile",
          type: "ts",
          size: "--",
          modify_time: "Oct7, 2022 2:20 PM(+08 00)",
          path: "Home",
          duration: "1s",
          status: "success"
        },
        {
          id: 4,
          filename: "plan",
          type: "folder",
          size: 0.3,
          modify_time: "Oct7, 2022 2:06 PM(+08 00)",
          path: "Home",
          duration: "1s",
          status: "success"
        },
        {
          id: 5,
          filename: "sub_01_case",
          type: "folder",
          size: "--",
          modify_time: "Oct7, 2022 2:36 PM(+08 00)",
          path: "Home",
          duration: "1s",
          status: "success"
        },
        {
          id: 6,
          filename: "Harry",
          type: "js",
          size: 0.62,
          modify_time: "Oct7, 2022 2:30 PM(+08 00)",
          path: "Home",
          duration: "1s",
          status: "success"
        },
        {
          id: 7,
          filename: "profile",
          type: "ts",
          size: "--",
          modify_time: "Oct7, 2022 2:20 PM(+08 00)",
          path: "Home",
          duration: "1s",
          status: "cancel"
        },
        {
          id: 8,
          filename: "plan",
          type: "folder",
          size: 0.3,
          modify_time: "Oct7, 2022 2:06 PM(+08 00)",
          path: "Home",
          duration: "1s",
          status: "success"
        }
      ],

      notifications: [
        {
          id: 1,
          status: "Success",
          filename: "index.html",
          duration: "1s",
          path: "Path: Home"
        },
        {
          id: 2,
          status: "Success",
          filename: "clolor.html",
          duration: ".2s",
          path: "Path: Home"
        },
        {
          id: 3,
          status: "Cancel",
          filename: "mylink.html",
          duration: "1s",
          path: "Path: Home"
        },
        {
          id: 4,
          status: "Success",
          filename: "index.html",
          duration: "1s",
          path: "Path: Home"
        }
      ],

      lists: [
        {
          id: 1,
          create_at: "2022-10-24 02:33:50",
          expire_at: "2022-10-31 02:33:50",
          uploads: "1",
          folder: "123/011/03"
        },
        {
          id: 2,
          create_at: "2022-10-24 02:33:50",
          expire_at: "2022-10-31 02:33:50",
          uploads: "3",
          folder: "123/011/03"
        },
        {
          id: 3,
          create_at: "2022-10-24 02:33:50",
          expire_at: "2022-10-31 02:33:50",
          uploads: "4",
          folder: "123/011/03"
        },
        {
          id: 4,
          create_at: "2022-10-24 02:33:50",
          expire_at: "2022-10-31 02:33:50",
          uploads: "2",
          folder: "123/011/03"
        },
        {
          id: 5,
          create_at: "2022-10-24 02:33:50",
          expire_at: "2022-10-31 02:33:50",
          uploads: "3",
          folder: "123/011/03"
        },
        {
          id: 6,
          create_at: "2022-10-24 02:33:50",
          expire_at: "2022-10-31 02:33:50",
          uploads: "1",
          folder: "test/011/03"
        },
        {
          id: 7,
          create_at: "2022-10-24 02:33:50",
          expire_at: "2022-10-31 02:33:50",
          uploads: "3",
          folder: "123/011/03"
        },
        {
          id: 8,
          create_at: "2022-10-24 02:33:50",
          expire_at: "2022-10-31 02:33:50",
          uploads: "2",
          folder: "test/011/03"
        }
      ]
    }
  },
  watch: {
    selectedCustomers() {
      console.log('fefe', this.selectedCustomers)
    },
    searchItem(val) {
      console.log('val', val)
      this.searchUser = this.users.filter((d) => {
        return (
          d.filename.includes(val)
        )


      })
      this.users = this.searchUser

      if (this.searchItem === '') {
        this.users = [
          {
            id: 1,
            filename: "sub_01_case",
            type: "folder",
            size: "--",
            modify_time: "Oct7, 2022 2:36 PM(+08 00)",
            path: "Home",
            duration: "1s",
            status: "success"
          },
          {
            id: 2,
            filename: "Harry",
            type: "js",
            size: 0.62,
            modify_time: "Oct7, 2022 2:30 PM(+08 00)",
            path: "Home",
            duration: "1s",
            status: "success"
          },
          {
            id: 3,
            filename: "profile",
            type: "ts",
            size: "--",
            modify_time: "Oct7, 2022 2:20 PM(+08 00)",
            path: "Home",
            duration: "1s",
            status: "success"
          },
          {
            id: 4,
            filename: "plan",
            type: "folder",
            size: 0.3,
            modify_time: "Oct7, 2022 2:06 PM(+08 00)",
            path: "Home",
            duration: "1s",
            status: "success"
          },
          {
            id: 5,
            filename: "sub_01_case",
            type: "folder",
            size: "--",
            modify_time: "Oct7, 2022 2:36 PM(+08 00)",
            path: "Home",
            duration: "1s",
            status: "success"
          },
          {
            id: 6,
            filename: "Harry",
            type: "js",
            size: 0.62,
            modify_time: "Oct7, 2022 2:30 PM(+08 00)",
            path: "Home",
            duration: "1s",
            status: "success"
          },
          {
            id: 7,
            filename: "profile",
            type: "ts",
            size: "--",
            modify_time: "Oct7, 2022 2:20 PM(+08 00)",
            path: "Home",
            duration: "1s",
            status: "cancel"
          },
          {
            id: 8,
            filename: "plan",
            type: "folder",
            size: 0.3,
            modify_time: "Oct7, 2022 2:06 PM(+08 00)",
            path: "Home",
            duration: "1s",
            status: "success"
          }
        ]
      }

      console.log('result', this.searchUser)
    }
  },
  created() {
    this.searchUser = this.users
  },

  methods: {
    addNew() {
      this.users.push({
        id: 10,
        filename: this.newFolder,
        type: "folder",
        size: 0.3,
        modify_time: "Oct7, 2022 2:06 PM(+08 00)",
        path: "Home",
        duration: "1s",
        status: "success"
      })
      this.newFolder = ''
      alert('sucess add item')
      this.open = false
    },
    deleteItem(event) {

      console.log('eve', event[0].filename)
      for (let i = 0; i < event.length; i++) {
        this.users.splice(this.users.findIndex(e => e === event[i]), 1)
      }


    },

  }


}


</script>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
}

.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}

.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}

.modal {
  position: fixed;
  z-index: 999;
  top: 20%;
  left: 50%;
  width: 300px;
  margin-left: -150px;
  background-color: white;
  padding: 30px;
}

.modal-bg {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 10;
}
</style>
