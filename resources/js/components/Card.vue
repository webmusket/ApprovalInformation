<template>
  <card class="flex flex-col">
    <div class="card"><table cellpadding="0" cellspacing="0" class="w-full"><tr><td class="align-top w-1/2 border-r border-b border-50"><a href="#" class="no-underline dim flex p-6"><div class="flex justify-center w-11 flex-no-shrink mr-6"><svg xmlns="http://www.w3.org/2000/svg" width="40" height="40" viewBox="0 0 40 40"><g id="Page-1" fill="none" fill-rule="evenodd"><g id="icon-resources" fill="var(--primary)" fill-rule="nonzero" transform="translate(0 -1)"><path id="Shape" d="M31.51 26.86l7.32 7.31c1.0110617 1.0110616 1.4059262 2.4847161 1.035852 3.865852-.3700742 1.3811359-1.4488641 2.4599258-2.83 2.83-1.3811359.3700742-2.8547904-.0247903-3.865852-1.035852l-7.31-7.32c-7.3497931 4.4833975-16.89094893 2.7645226-22.21403734-4.0019419-5.3230884-6.7664645-4.74742381-16.4441086 1.34028151-22.53181393C11.0739495-.11146115 20.7515936-.68712574 27.5180581 4.63596266 34.2845226 9.95905107 36.0033975 19.5002069 31.52 26.85l-.01.01zm-3.99 4.5l7.07 7.05c.7935206.6795536 1.9763883.6338645 2.7151264-.1048736.7387381-.7387381.7844272-1.9216058.1048736-2.7151264l-7.06-7.07c-.8293081 1.0508547-1.7791453 2.0006919-2.83 2.83v.01zM17 33c8.2842712 0 15-6.7157288 15-15 0-8.28427125-6.7157288-15-15-15C8.71572875 3 2 9.71572875 2 18c0 8.2842712 6.71572875 15 15 15zm0-2C9.82029825 31 4 25.1797017 4 18S9.82029825 5 17 5c7.1797017 0 13 5.8202983 13 13s-5.8202983 13-13 13zm0-2c6.0751322 0 11-4.9248678 11-11S23.0751322 7 17 7 6 11.9248678 6 18s4.9248678 11 11 11z"></path></g></g></svg></div> <div><h3 class="mb-3 text-90 font-bold text-lg">Total Approval</h3> <p class="text-90 leading-normal">

    <h1>{{total[0]}}</h1>

    </p></div></a></td> <td class="align-top w-1/2 border-b border-50"><a href="#" class="no-underline dim flex p-6"><div class="flex justify-center w-11 flex-no-shrink mr-6"><svg xmlns="http://www.w3.org/2000/svg" width="44" height="44" viewBox="0 0 44 44"><g id="Page-1" fill="none" fill-rule="evenodd"><g id="icon-actions" fill="var(--primary)" fill-rule="nonzero"><path id="Shape" d="M22 44C9.8497355 44 0 34.1502645 0 22S9.8497355 0 22 0s22 9.8497355 22 22-9.8497355 22-22 22zm0-2c11.045695 0 20-8.954305 20-20S33.045695 2 22 2 2 10.954305 2 22s8.954305 20 20 20zm3-24h5c.3638839-.0007291.6994429.1962627.8761609.5143551.176718.3180924.1666987.707072-.0261609 1.0156449l-10 16C20.32 36.38 19 36 19 35v-9h-5c-.3638839.0007291-.6994429-.1962627-.8761609-.5143551-.176718-.3180924-.1666987-.707072.0261609-1.0156449l10-16C23.68 7.62 25 8 25 9v9zm3.2 2H24c-.5522847 0-1-.4477153-1-1v-6.51L15.8 24H20c.5522847 0 1 .4477153 1 1v6.51L28.2 20z"></path></g></g></svg></div> <div><h3 class="mb-3 text-90 font-bold text-lg">Pending Approval</h3> <p class="text-90 leading-normal">
    <h1>{{total[0] - total[1]}}</h1>
    </p></div></a></td></tr></table></div>
  <!--  <div class="flex mb-4">
  <div class="w-1/3 bg-gray-400 h-12">
    <div role="alert">
      <div class="bg-red-500 text-white font-bold rounded-t px-4 py-2">
        Danger
      </div>
      <div class="border border-t-0 border-red-400 rounded-b bg-red-100 px-4 py-3 text-red-700">
        <p>Something not ideal might be happening.</p>
      </div>
    </div>
  </div>
  <div class="w-1/3 bg-gray-500 h-12">
    <div role="alert">
      <div class="bg-red-500 text-white font-bold rounded-t px-4 py-2">
        Danger
      </div>
      <div class="border border-t-0 border-red-400 rounded-b bg-red-100 px-4 py-3 text-red-700">
        <p>Something not ideal might be happening.</p>
      </div>
    </div>
  </div>
  <div class="w-1/3 bg-gray-400 h-12">
    <div role="alert">
      <div class="bg-red-500 text-white font-bold rounded-t px-4 py-2">
        Danger
      </div>
      <div class="border border-t-0 border-red-400 rounded-b bg-red-100 px-4 py-3 text-red-700">
        <p>Something not ideal might be happening.</p>
      </div>
    </div>
  </div>
  </div> -->
  </card>
</template>

<script>
  export default {
    props: [
    'card',
    // The following props are only available on resource detail cards...
    // 'resource',
    // 'resourceId',
    // 'resourceName',
    ],
    data() {
        return {
            total : {},

        }
    },
    mounted () {
    //
    },
    created(){
        //console.log(window.location.pathname.split('/')[1])
        
        const uri = `/getconfirmation`;
        Nova.request().get(uri).then((response) => {
          //console.log(response.data);
            this.total = response.data;
        });

    },
  }
</script>
