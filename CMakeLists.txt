cmake_minimum_required(VERSION 3.10)
project (sample VERSION 1.0)

SET(CMAKE_C_FLAGS "-fno-stack-protector -Wall -Wextra -Wno-unused-parameter -g -O3 -std=gnu11 -march=native -msse4.2 -Wno-deprecated-declarations -Wno-address-of-packed-member")

SET(DPDK_LIBS
  rte_net
  rte_ethdev
  rte_mbuf
  rte_pmd_bond
  rte_eal
  rte_mempool
  rte_mempool_ring
  rte_cfgfile
  rte_pmd_i40e
  rte_cmdline
)

INCLUDE_DIRECTORIES(
        /usr/include/dpdk
)

LINK_DIRECTORIES(
        /usr/include/dpdk
)

add_executable (simple simple.c)
TARGET_LINK_LIBRARIES(simple ${DPDK_LIBS})
