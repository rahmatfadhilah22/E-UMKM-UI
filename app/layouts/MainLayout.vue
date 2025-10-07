<script setup lang="ts">
import type { NavigationMenuItem } from '@nuxt/ui'

const items: NavigationMenuItem[][] = [[
  {
    label: 'Dashboard',
    icon: 'i-lucide-house',
    children: [
      { label: 'Ringkasan', to: '/dashboard/ringkasan' },
      { label: 'Target Penjualan', to: '/dashboard/targetpenjualan' }
    ]
  },
  {
    label: 'POS',
    icon: 'i-lucide-shopping-cart',
    children: [
      { label: 'Transaksi', to: '/pos/transaksi' },
      { label: 'Riwayat Transaksi', to: '/pos/riwayat' }
    ]
  },
  {
    label: 'Product',
    icon: 'i-lucide-package',
    children: [
      { label: 'Kelola Produk', to: '/product' },
      { label: 'Kategori Produk', to: '/master/kategori' }
    ]
  },
  {
    label: 'Inventori',
    icon: 'i-lucide-box',
    children: [
      { label: 'Stok Barang', to: '/inventori/stok' },
      { label: 'Stok Masuk', to: '/inventori/masuk' },
      { label: 'Stok Keluar', to: '/inventori/keluar' }
    ]
  },
  {
    label: 'Hitung HPP',
    icon: 'i-lucide-calculator',
    children: [
      { label: 'Input Harga Pokok', to: '/hpp/input' },
      { label: 'Simulasi Harga', to: '/hpp/simulasi' }
    ]
  },
  {
    label: 'Laporan',
    icon: 'i-lucide-bar-chart-2',
    children: [
      { label: 'Produk', to: '/laporan/produk' },
      { label: 'Penjualan', to: '/laporan/penjualan' },
      { label: 'Arus Kas', to: '/laporan/aruskas' }
    ]
  }
], [
  {
    label: 'Settings',
    icon: 'i-lucide-settings',
    children: [
      { label: 'Profile Setting', to: '/settings/profilesetting' },
      { label: 'Users & Roles', to: '/settings/users' },
      { label: 'Logout', to: '/settings/logout' }
    ]
  }
]]

</script>

<template>
  <UDashboardGroup storage="local" storage-key="main-layout">
    <div class="flex flex-1 min-h-dvh">
      <!-- Sidebar -->
      <UDashboardSidebar collapsible resizable :ui="{ footer: 'border-t border-default' }">
        <template #header="{ collapsed }">
          <div v-if="!collapsed" class="h-5 flex items-center font-semibold">
            E-UMKM
          </div>
          <UIcon v-else name="i-simple-icons-nuxtdotjs" class="size-5 text-primary mx-auto" />
        </template>

        <template #default="{ collapsed }">
          <!-- blok atas -->
          <UNavigationMenu :collapsed="collapsed" :items="items[0]" orientation="vertical" />

          <!-- blok bawah, berisi Settings accordion -->
          <UNavigationMenu :collapsed="collapsed" :items="items[1]" orientation="vertical" class="mt-auto" />
        </template>

        <template #footer="{ collapsed }">
          <UButton :avatar="{ src: 'https://github.com/benjamincanac.png' }" :label="collapsed ? undefined : 'Benjamin'"
            color="neutral" variant="ghost" class="w-full" :block="collapsed" />
        </template>
      </UDashboardSidebar>

      <!-- konten -->
      <UMain class="p-4">
        <NuxtPage />
      </UMain>
    </div>
  </UDashboardGroup>
</template>
